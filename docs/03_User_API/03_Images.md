## List all images

*Digital Ocean equivalent: /images/*

~~~ruby
Oceanarium::images
# or
Oceanarium::images(filter)
~~~

Returns Array of all images.

There are two types of images: system (created by Digital Ocean, avaliable to all users) and user's images ('my_images', avaliable only for selected user). This command will show you all images, including system and user's one.

~~~ruby
> Oceanarium::images
=>  [#<Oceanarium::Image:0x007f1257db5180 @object={"id"=>100500, "name"=>"test_user_image", "slug"=>nil, "distribution"=>"Debian"}, @id=100500, @name="test_user_image", @slug=nil, @distribution="Debian">, #<Oceanarium::Image:0x007f1257db4ff0 @object={"id"=>1601, "name"=>"CentOS 5.8 x64", "slug"=>nil, "distribution"=>"CentOS"}, @id=1601, @name="CentOS 5.8 x64", @slug=nil, @distribution="CentOS">, #<Oceanarium::Image:0x007f1257db4f28 @object={"id"=>1602, "name"=>"CentOS 5.8 x32", "slug"=>nil, "distribution"=>"CentOS"}…] # and so on
~~~

All objects in this array are valid Image objects, responding to anything that listed below.

### List only user's images

*Digital Ocean equivalent: */images/?filter=my_images*

~~~ruby
> Oceanarium.images('my_images')
=> [#<Oceanarium::Image:0x007f1257dfcbe8 @object={"id"=>100500, "name"=>"test_user_image", "slug"=>nil, "distribution"=>"Debian"}, @id=100500, @name="test_user_image", @slug=nil, @distribution="Debian">, #<Oceanarium::Image:0x007f1257dfcb20 @object={"id"=>100501, "name"=>"another_test_user_image", "slug"=>nil, "distribution"=>"Ubuntu"}, @id=100500, @name="another_test_user_image", @slug=nil, @distribution="Ubuntu">]
~~~

Returns array with only user's images.

### List only system images

*Digital Ocean equivalent: */images/?filter=global*

~~~ruby
> Oceanarium::images('global')
=> [#<Oceanarium::Image:0x007f1257e3f330 @object={"id"=>1601, "name"=>"CentOS 5.8 x64", "slug"=>nil, "distribution"=>"CentOS"}, @id=1601, @name="CentOS 5.8 x64", @slug=nil, @distribution="CentOS">, #<Oceanarium::Image:0x007f1257e3f268 @object={"id"=>1602, "name"=>"CentOS 5.8 x32", "slug"=>nil, "distribution"=>"CentOS"}, @id=1602, @name="CentOS 5.8 x32", @slug=nil, @distribution="CentOS">…] # and so on
~~~

Returns array with only system images, avaliable to all users of Digital Ocean.

## Image

*Digital Ocean equivalent: */images/[image_id]*

~~~ruby
Oceanarium::image(image_id)
~~~

Returns an Image object with selected ID. Image is a Ruby object, which have some useful parameters.

~~~ruby
# valid image id
> Oceanarium::image(100500)
=> #<Oceanarium::Image:0x007f1257e56aa8 @object={"id"=>100500, "name"=>"Wordpress on Ubuntu 12.10", "slug"=>nil, "distribution"=>"Ubuntu"}, @id=100500, @name="Wordpress on Ubuntu 12.10", @slug=nil, @distribution="Ubuntu">
# invalid image id
> Oceanarium::image(201000)
=> #<Oceanarium::Image:0x007f1257e849f8 @object=nil, @id=nil>
~~~

### Image object parameters

### id

~~~ruby
> Oceanarium::image(100500).id
=> 100500
~~~

Returns an Image ID. Numeric.

### name

~~~ruby
> Oceanarium::image(100500).name
=> "Wordpress on Ubuntu 12.10"
~~~

Returns an Image name. String.

### slug

Currently returns nil. Will be described after Digital Ocean will become to using this parameter for something useful.

### distribution

~~~ruby
> Oceanarium::image(100500).distribution
=> "Ubuntu"
~~~

Returns a common short name (without versions, codenames, et cetera) for Image distro. String.

### Actions on image

#### destroy

*Digital Ocean equivalent: */images/[image_id]/destroy/*

~~~ruby
> Oceanarium::image(100500).destroy
=> "OK"
~~~

Destroying an image. Note: you can't destroy system images, unless you're a Digital Ocean administrator (but Oceanarium is not for they one!) ;) Returns "OK" if you're OK, else — "ERROR" or "Error".

#### transfer

*Digital Ocean equivalent: /images/[image_id]/transfer?region_id=[region_id]*

~~~ruby
> Oceanarium::image(100500).transfer(region_id)
=> "OK"
~~~

Transfering image to new region (datacenter: see Regions article for more explanation).

Parameters:

* **region_id** — ID of Region (datacenter). For getting all avaliable Regions just type <pre>Oceanarium::regions</pre>.