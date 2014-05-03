TwitterOAuth
============
This class is a union of "abraham/twitteroauth"(owner), 
"ruudk/twitteroauth"(php 5.3 and namespaces) and 
(robhaswell/twitteroauth) (upload image).

- The directories are structured and the class uses PHP5.3 namespaces.
- Included upload image using 'statuses/update_with_media' (robhaswell/twitteroauth).

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist newerton/twitter-oauth "dev-master"
```

or add

```
"newerton/twitter-oauth": "dev-master"
```

to the require section of your `composer.json` file.


Usage
-----

Once the extension is installed, simply use it in your code by  :

```php
<?php
    use newerton\twitteroauth\TwitterOAuth;

    /**
     * Array with the OAuth tokens provided by Twitter when you create application
     */
    $config = [
            'consumer_key' => 'Consumer key',
            'consumer_secret' => 'Consumer secret',
            'oauth_token' => 'Access token',
            'oauth_token_secret' => 'Access token secret'
    ];

    /**
     * Instantiate TwitterOAuth class with set tokens
     */
    $tw = new TwitterOAuth($config);

    //send update status
    $response = $connection->post('statuses/update', ['status' => 'Posted by Class TwitterOAuth']);

    //send update status with upload image
    $file = realpath('./path/to/image/twitter.jpg');
    $params = array(
        'media[]' => "@{$file}",
        'status' => 'Posted by Class TwitterOAuth'
    );
    $response = $connection->upload('statuses/update_with_media', $params);
```