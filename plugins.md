# WordPress to Textpattern plugin

## Plugins development

### DB management methods/functions [a→z]

* [`WP DB`](https://codex.wordpress.org/Database_Description) → [`Txp DB`](https://docs.textpattern.com/development/database-schema-reference);
* [`$wpdb->delete()`](https://codex.wordpress.org/Class_Reference/wpdb#DELETE_Rows) → [`safe_delete()`](https://github.com/textpattern/textpattern/blob/82552af318777edd87f89027b2e5bac7c1b9e4f1/textpattern/lib/txplib_db.php#L420);
* [`$wpdb->insert()`](https://codex.wordpress.org/Class_Reference/wpdb#INSERT_row) → [`safe_insert()`](https://github.com/textpattern/textpattern/blob/82552af318777edd87f89027b2e5bac7c1b9e4f1/textpattern/lib/txplib_db.php#L463);
* [`$wpdb->get_row()`](https://codex.wordpress.org/Class_Reference/wpdb#SELECT_a_Row) → [`safe_row()`](https://github.com/textpattern/textpattern/blob/82552af318777edd87f89027b2e5bac7c1b9e4f1/textpattern/lib/txplib_db.php#L895);
* [`$wpdb->get_var()`](https://codex.wordpress.org/Class_Reference/wpdb#SELECT_a_Variable) → [`safe_field()`](https://github.com/textpattern/textpattern/blob/82552af318777edd87f89027b2e5bac7c1b9e4f1/textpattern/lib/txplib_db.php#L809);
* [`$wpdb->prefix`](https://codex.wordpress.org/Class_Reference/wpdb) → [`safe_pfx()`](https://github.com/textpattern/textpattern/blob/82552af318777edd87f89027b2e5bac7c1b9e4f1/textpattern/lib/txplib_db.php#L247);
* [`$wpdb->query()`](https://codex.wordpress.org/Class_Reference/wpdb#Running_General_Queries) → [`safe_query()`](https://github.com/textpattern/textpattern/blob/82552af318777edd87f89027b2e5bac7c1b9e4f1/textpattern/lib/txplib_db.php#L370);
* [`$wpdb->replace()`](https://codex.wordpress.org/Class_Reference/wpdb#REPLACE_row) → [`safe_upsert()`](https://github.com/textpattern/textpattern/blob/82552af318777edd87f89027b2e5bac7c1b9e4f1/textpattern/lib/txplib_db.php#L493);
* …

### Custom tags creation [a→z]

* [`add_shortcode()`](https://codex.wordpress.org/Function_Reference/add_shortcode) → [`Txp::get('\Textpattern\Tag\Registry')->register()`](https://github.com/textpattern/textpattern/blob/82552af318777edd87f89027b2e5bac7c1b9e4f1/textpattern/vendors/Textpattern/Tag/Registry.php#L44);
* [`shortcode_atts()`](https://codex.wordpress.org/Function_Reference/shortcode_atts) → [`lAtts()`](https://github.com/textpattern/textpattern/blob/37f792ea84e3e35aab60415e9267d273b5a0cc6c/textpattern/lib/txplib_misc.php#L2156).
* …

## Hooks

* [`add_action()`](https://developer.wordpress.org/reference/functions/add_action/) → [`register_callback()`](https://docs.textpattern.com/development/#function-register_callback);
* [`do_action()`](https://developer.wordpress.org/reference/functions/do_action/) → [`callback_event()`](https://github.com/textpattern/textpattern/blob/dev/textpattern/lib/txplib_misc.php#L1895);
* …
