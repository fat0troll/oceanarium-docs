Before any action, you must configure Oceanarium.

Digital Ocean uses two tokens to authenticate user — API key and Client ID. If they're wrong, any API call will return "ERROR". So, Oceanarium needs this tokens to work as expected.

## In Ruby shell

Just type this:

~~~ruby
Oceanarium::Config.api_key = "your_api_key"
Oceanarium::Config.client_id = "your_client_id"
~~~

Voila! You're ready to use Oceanarium :)

## In Rails

In your Rails application create file inside config/initializers (for example — oceanarium.rb) with following content:

~~~ruby
Oceanarium::Config.api_key = "your_api_key"
Oceanarium::Config.client_id = "your_client_id"
~~~

Now you're ready to use Oceanarium in your Rails application.

## Advanced configuration parameters

There is one advanced parameter — api_url. If you want to use this gem with site, which provides API similar to Digital Ocean, you must override this setting. By default api_url returns *"https://api.digitalocean.com/"*. If you want to use custom URL, just invoke this:

~~~ruby
Oceanarium::Config.api_url = "your_custom_api_url"
~~~

Note: authors of this gem doesn't support this function. Use it at your own risk, and don't send any bug reports when using custom API URL!
