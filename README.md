# Gatsby Wordpress Docker Template 🐳

## 🚀 Quick start

1.  Install [Docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04)

2.  Create a `.env` file and add `WORDPRESS_URL=0.0.0.0`

3.  **To Start developing** set up your local environment by running this command:

    `docker-compose -f docker-compose.yml -f docker-compose.dev.yml up` or `npm run docker:dev`
    
    This command creates the images and starts the containers. (NodeJS, Wordpress, MySQL and Gatsby)
    Running it again only starts up the containers.

4.  To shut down the environment use: `docker-compose down` or `npm run docker:down`

5.  Make sure to run `npm install` to install dependancies

    
## 🧐 What's next?

Setup your local [Wordpress](https://localhost:8080/) site :

1. Make an initial installation

2. Add this line to wordpress/engine/wp-config.php to prevent FTP issue: `define('FS_METHOD', 'direct');`

3. Enable Wordpress plugins ( ACF to REST API, Advanced Custom Fields, Custom Post Type UI, WP REST API Menus )

4. Setup `pretty permalinks` by going to **Settings** => **Permalinks** => choose '**Post Name**' and save.

5. Restart containers to properly initialize Gatsby

6. Go to the [Graph*i*QL](http://localhost:8000/__graphql) editor and try out queries to make sure everything is working:

```
{
  allWordpressPost {
    edges {
      node {
        id
        slug
        title
        content
        excerpt
        date
        modified
      }
    }
  }
}
```

- Try out the [Gatsby Site](http://localhost:8000)

## Additional Info

After wordpress setup, the `wordpress/engine` folder directly binds to the wordpress container. You can easily modify it locally.

**!!!** Note that the `wordpress/plugins_for_setup` used to copy initial plugins for the setup should not be edited after initialization.