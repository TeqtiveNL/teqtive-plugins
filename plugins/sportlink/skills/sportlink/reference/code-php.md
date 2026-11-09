# Codevoorbeelden: PHP en WordPress

De ClientID staat in de serverconfig en wordt alleen server-side gelezen. Bij WordPress is dat een constante in `wp-config.php` (buiten de webroot of buiten versiebeheer), in plain PHP de omgevingsvariabele `SPORTLINK_CLIENT_ID`.

**Naamgeving:** functies, variabelen en commentaar zijn Engels, zoals `sportlink_fetch_upcoming_matches()`. Alleen de velden uit de API houden hun Nederlandse naam (`poulecode`, `teamnaam`).

## WordPress: helper met caching

```php
<?php
// wp-config.php (keep this file out of version control):
// define( 'SPORTLINK_CLIENT_ID', getenv( 'SPORTLINK_CLIENT_ID' ) );

/**
 * Fetch a Sportlink Club.Dataservice article, cached as a transient.
 *
 * @return array|WP_Error Decoded JSON, or WP_Error on failure.
 */
function sportlink_fetch( string $article, array $params = [], int $ttl = 300 ) {
    if ( ! defined( 'SPORTLINK_CLIENT_ID' ) || ! SPORTLINK_CLIENT_ID ) {
        return new WP_Error( 'sportlink_no_client_id', 'SPORTLINK_CLIENT_ID is not configured' );
    }

    $cache_key = 'sportlink_' . md5( $article . wp_json_encode( $params ) );
    $cached    = get_transient( $cache_key );
    if ( false !== $cached ) {
        return $cached;
    }

    $url = add_query_arg(
        array_merge( [ 'client_id' => SPORTLINK_CLIENT_ID ], $params ),
        'https://data.sportlink.com/' . rawurlencode( $article )
    );

    $response = wp_remote_get( $url, [ 'timeout' => 10 ] );
    if ( is_wp_error( $response ) ) {
        return $response;
    }

    $body = json_decode( wp_remote_retrieve_body( $response ), true );
    // Sportlink returns errors as { "error": { "message", "code" } }
    if ( isset( $body['error'] ) ) {
        return new WP_Error( 'sportlink_' . $body['error']['code'], $body['error']['message'] );
    }

    set_transient( $cache_key, $body, $ttl );
    return $body;
}
```

## Shortcode: stand van een poule

```php
<?php
// Usage: [sportlink_stand poulecode="123456"]
add_shortcode( 'sportlink_stand', function ( $atts ) {
    $atts  = shortcode_atts( [ 'poulecode' => '' ], $atts );
    $rows  = sportlink_fetch( 'poulestand', [ 'poulecode' => $atts['poulecode'] ] );
    if ( is_wp_error( $rows ) || empty( $rows ) ) {
        return '<p>Stand niet beschikbaar.</p>';
    }

    $html = '<table class="sportlink-stand"><tr><th>#</th><th>Team</th><th>G</th><th>P</th></tr>';
    foreach ( $rows as $row ) {
        $html .= sprintf(
            '<tr><td>%d</td><td>%s</td><td>%d</td><td>%d</td></tr>',
            (int) $row['positie'],
            esc_html( $row['teamnaam'] ),
            (int) $row['gespeeldewedstrijden'],
            (int) $row['punten']
        );
    }
    return $html . '</table>';
} );
```

Escape elke waarde uit de API bij het tonen (`esc_html`, `esc_attr`, `esc_url`). Gebruik de veldnamen uit het artikelbestand (*Uitvoervelden*). Een lege stand kan een bondsregel zijn, zoals de jongste jeugd bij de KNVB: zie [bonden.md](bonden.md).

## Plain PHP

```php
<?php
function sportlink_fetch_plain( string $article, array $params = [] ): array {
    $clientId = getenv( 'SPORTLINK_CLIENT_ID' );
    if ( ! $clientId ) {
        throw new RuntimeException( 'SPORTLINK_CLIENT_ID is not set' );
    }
    $url  = 'https://data.sportlink.com/' . rawurlencode( $article ) . '?'
          . http_build_query( array_merge( [ 'client_id' => $clientId ], $params ) );
    $body = json_decode( file_get_contents( $url ) ?: '{}', true );
    if ( isset( $body['error'] ) ) {
        throw new RuntimeException( $body['error']['message'], (int) $body['error']['code'] );
    }
    return $body;
}
```

Richtwaarden voor caching: een paar minuten voor `programma`, `uitslagen` en `poulestand`; uren voor `clubgegevens`, `teams` en `keuzelijst-*`.
