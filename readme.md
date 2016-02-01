#Cloudflare API PHP wrapper

I'm gradually using more of Cloudflare's functionality snd adding more features. Please do submit any specific requests as it may be something I already know I need soon and can implement it.


##Installation
Installation should be done via composer, details of how to install composer can be found at https://getcomposer.org/


Add `"mcstutterfish/cloudflare": "dev-feature"` to your `composer.json` file

Add the following to the end of your `composer.json` file as well (don't forget the comma before the last object)
```javascript    
"repositories": [
      {
        "type": "vcs",
        "url": "https://github.com/zOxta/cloudflare"
      }
    ]
```

Run `composer update` to install the latest version.

##Usage

In situations where you want to make multiple calls to the API across different services it's easier to create a connection to the api first and then pass that around the other services e.g.

```php
    use Cloudflare;
    use Cloudflare\Zone\Dns;

    // Create a connection to the Cloudflare API which you can
    // then pass into other services, e.g. DNS, later on
    $client = new Cloudflare\Api('email@example.com', 'API_KEY');

    // Create a new DNS record
    $dns = new Cloudflare\Dns($client);
    $dns->create('12345678901234567890', 'TXT', '127.0.0.1', 120);
```

If you are just performing a single action then you can connect to the API directly when you instantiate the class e.g.
```php
    use Cloudflare;

    // Create a connection to the Cloudflare API which you can
    // then pass into other services, e.g. DNS, later on
    $dns = new Cloudflare\Zone\Dns('email@example.com', 'API_KEY');
    $dns->create('12345678901234567890', 'TXT', '127.0.0.1', 120);
```

#License
MIT
