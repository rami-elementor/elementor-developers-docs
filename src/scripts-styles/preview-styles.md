# Preview Styles

When you develop addons that extend [Elementor Preview](/editor/elementor-preview) and you need to register custom stylesheets, use the `elementor/preview/enqueue_styles` action hook which is fired when Elementor Preview styles are registered and enqueued.

## Registering Preview Styles

Register and enqueue custom stylesheets after Elementor preview styles are registered and enqueued:

```php {11}
function my_plugin_preview_styles() {

	wp_register_style( 'preview-style-1', plugins_url( 'assets/css/preview-style-1.css', __FILE__ ) );
	wp_register_style( 'preview-style-2', plugins_url( 'assets/css/preview-style-2.css', __FILE__ ), [ 'external-framework' ] );
	wp_register_style( 'external-framework', plugins_url( 'assets/css/libs/external-framework.css', __FILE__ ) );

	wp_enqueue_style( 'preview-style-1' );
	wp_enqueue_style( 'preview-style-2' );

}
add_action( 'elementor/preview/enqueue_styles', 'my_plugin_preview_styles' );
```