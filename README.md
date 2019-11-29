# Best Practices and Coding Standards for custom builds
 
1. Develop using php 7.2
1. Use our [ git flow proceedure ](https://github.com/pixelstorm/coding_guidlnes_custom_builds/blob/master/git-flow)
1. Use [ Underscores ](https://underscores.me/) as the starter theme.
1. No inline code, no hardcoding content into theme files, no code is to be exposed to the client in the admin area.
1. Use svgs for icons and logos where posible.
1. Develop locally deploy to a NOFOLLOW staging url.
1. Develop with define('wp_debug', true); 
1. Build a static, fully responsive html templates with html / scss first before implementing advanced custom fields and dynamic data functionality.
1. Use Advanced Custom fields & Hookturn plugins to build custom content areas and fields 

1. All media/images are to be loaded into the wp-content/uploads directory and accessible via to the wp-admin
1. Create [ custom image sizes ](https://developer.wordpress.org/reference/functions/add_image_size/) for all components that use images.

### Css
1. Use bourbon.io and neat.io
1. Use a BEM css metholodgy
1. Dont use id's for css selectors. Only use ids for js
1. Use fluid typography mixin for type, padding, margins etc to match mobile and desktop designs accurately. [fluid type mixin](https://codepen.io/MadeByMike/pen/GmBLKo)
1. When deploying to production, compress your css files into one minified file

### js
1. When deploying to production, Compress your js files into one minified file

### html
HTML5 elements and markup to be used according to best practices
 
### WordPress Setup
1. Choose a unique relavent username(not admin)
1. Ensure comments are disabled
1. Disable RSS feeds
1. Use a unique table prefix 
1. Use a pixelstorm email address as the setup email address
1. Remove 'just another wordpress site' from the strapline - replace with company strapline if they have one.
1. Replace wp logo with client logo on the wordpress admin login screen
1. Delete, hello world post, sample page and hello dolly and akismet
1. Disable comments on new posts in site settings
1. Set utc time to +10 and week starts on Sunday 


## Plugins – List of Approved Plugins for production site
Please discuss if when adding a plugin that is not part of this list.
 
And please, NEVER modify a plugin directly. Use functions.php in the theme or create a custom plugin.
 
1. Advanced Custom Fields Pro (we have a premium license)
1. Gravity Forms (we have a premium license)
1. Yoast
1. Woocommerce


1. Prefix all functions with pxs_ and tables with a unique white_label prefix.
 
# Custom Coding
1. Prefix all functions with pxs_ and tables with a unique white_label prefix.
1. Provide comments for functions and templates.
1. follow html 5 best practices
1. Site must validate on [wave]( http://wave.webaim.org/ ) and [ csslint ](http://csslint.net/)

# Filestructure 
```
 theme (custom theme) 
  | dev  
    - package.json  
    |- node_modules (exclude from commits) 
    |- sass 
	 |- bourbon 
	 |- neat  
	 |- _custom.scss (main stylesheet)
	 |- _mixins.scss 
```

The dev file is ommitted from upload to the staging and production server so DONT include any production css files in the dev directory

#git 
1. Install git in the custom theme directory
1. Checkout feature branches when working on a new feature
1. Deploy your branch through beanstalk
1. Once your feature branch is approved - merge it into your master repo. 


# Testing in browser stack (login supplied)

1. Ios iphone5 and up, Ipad all versions 
1. Android S4 and up, Galaxy 3 and up, Galaxy SS mini 
1. Internet Explorer 11 and up 
1. latest versions of Firefox, Chrome and Safari 

### We adhere to wordpress best practices broadly defined here:

http://codex.wordpress.org/working_with_wordpress  http://codex.wordpress.org/developer_documentation  

1. All code should be compatible with the latest version of wordpress.

1. Follow the wordpress coding standards.  http://codex.wordpress.org/wordpress_coding_standards

1. Data must be validated and sanitized on input and escaped on output.

1. Avoid direct calls to php scripts in your theme and do not try to load the wordpress environment on your own.

1. Ensure code will be both backward-compatible and future-proof using the wordpress core apis.

1. Encapsulate all code within a theme and plugins – do not scatter scripts or other assets in other locations.

1. Use standard wordpress theme development practices. avoid overriding the native theming engine with a third party engine (e.g. mustache or smarty) or an unusual framework.

1. Avoid modifying the server side page rendering based on visitor or other one off properties for unauthenticated visitors (this is imperative in environments with page caching enabled).

1. Avoid interacting with cookies on the server side. client side interaction (javascript) is fine.

1. Avoid direct interaction with database tables (sql queries). strongly avoid scripts that alter the database structure by, for example, adding or altering database fields, and creating new tables.

1. Clean up after yourself: remove unused files and directories and any unused code fragments or debugging comments.

1. Adhere to a consistent coding style.

*under no circumstances should you ever edit wordpress core files or plugin files directly. 
if you need to modify a plugin, hook from the theme’s functions.php file or create a custom plugin.

### Database

Avoid direct interaction with database tables (SQL queries). 
In reality, 9 out of 10 times, the same result can be accomplished by using an official WordPress function or API, which often include sophisticated caching while ensuring forwards compatibility.

Strongly avoid scripts that alter the database structure by, for example, adding or altering database fields, and creating new tables. In most cases, WordPress’s sophisticated custom post types, taxonomies, options, and meta data API’s can accomplish the same result with superior security and performance (especially in cache-enabled environments). Scripts that alter the database structure require dramatically more time to audit, review, and test.

In the event that database interaction is truly essential, WordPress provides a class of functions for all database manipulations. The class is called wpdb and is loosely based on the ezSQL class written and maintained by Justin Vincent.

Learn more about the $wpdb Object: http://codex.wordpress.org/Class_Reference/wpdb

### Validation and Sanitization

#### Input Validation
To validate is to ensure the data you’ve requested of the user matches what they’ve submitted. There are several core methods you can use for input validation; usage obviously depends on the type of fields you’d like to validate.
More
information:http://codex.wordpress.org/Validating_Sanitizing_and_Escaping_User_Data#Validating:_Checki ng_User_Input

#### Escape Output
For security on the other end of the spectrum, we have escaping. To escape is to take the data you may already have and help secure it prior to rendering it for the end user.
More information: http://codex.wordpress.org/Validating_Sanitizing_and_Escaping_User_Data#Escaping:_Securing_Output
