# Database for environments

1. Export database from phpmyadmin in production environment

1. Open the exported`.sql` file and make note of the prefix on tables.
Example, find something like:

    ```sql
    CREATE TABLE `wp_7umsd4_commentmeta`
    ```

    The prefix is `wp_7umsd4_`.

1. Run WP Local sites and select the Marmalade installation

1. Go to Database tab and click "Open AdminerEvo"

1. Delete all tables created automatically by WP Local Sites

1. Updated the WordPress `wp-config.php`.
Change the value of `$table_prefix` to the prefix noted in step 2.
ie: `$table_prefix = 'wp_7umsd4_';`

1. Import the database exported in step 1

1. Open site shell from WP Local Sites and run the following command (ensure wp cli is installed, see [WP Cli installation](#wp-cli-installation)):

   ```sh
     wp search-replace --all-tables production-site-url local-site-url
     #example wp search-replace --all-tables https://api.marmaladians.com https://marmalade-cms.local
   ```

1. If you need to run the database in a Database Management application, run this command to find the database port for connection ([read more](https://community.localwp.com/t/how-can-i-connect-to-mysql-using-tcp-ip-rather-than-a-socket-on-macos-linux/21220)):

   ```sh
     mysql -e "CREATE USER 'root'@'127.0.0.1' IDENTIFIED BY 'root'; GRANT ALL ON *.* TO 'root'@'127.0.0.1';"
   ```

   ```sh
     mysql -e "SHOW VARIABLES WHERE Variable_name = 'port';"
   ```

## WP Cli Installation

1. For local environments you need install WP Cli in your local machine [Reference URL](https://make.wordpress.org/cli/handbook/guides/installing/)

   ```sh
     curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
   ```

2. Then, check if it works

   ```sh
     php wp-cli.phar --info
   ```

3. To be able to type just `wp`, instead of php `wp-cli.phar`, you need to make the file executable and move it to somewhere in your PATH. For example:

   ```sh
     chmod +x wp-cli.phar
     sudo mv wp-cli.phar /usr/local/bin/wp
   ```
