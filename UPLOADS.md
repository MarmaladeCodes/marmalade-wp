# Media from production

1) Download plugin: BE Media from Production

2) Install Plugin

3) Activate Plugin

4) Include this constant in the file wp-config.php

  ```sh
    define( 'BE_MEDIA_FROM_PRODUCTION_URL', 'https://api.marmaladians.com' );
  ```

  or include this in functions.php (recommended for this installation)

  ```sh
    add_filter( 'be_media_from_production_url', function() {
      return 'https://api.marmaladians.com';
    });
  ```
