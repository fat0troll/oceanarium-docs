## List all droplets

*Digital Ocean API equivalent: /droplets/*

~~~ruby
Oceanarium::droplets
~~~

Returns an Array with all droplets, registered to user which API key and Client ID is used.

~~~ruby
> Oceanarium::droplets
=> [#<Oceanarium::Droplet:0x007fb29ea827c8 @object={"id"=>100500, "name"=>"example.com", "image_id"=>100501, "size_id"=>1, "region_id"=>1, "backups_active"=>nil, "ip_address"=>"192.0.2.1", "status"=>"active", "created_at"=>"2013-07-04T15:39:49Z"}, @id=100500, @name="example.com", @image_id=100501, @size_id=1, @region_id=1, @backups_active=nil, @ip_address="192.0.2.1", @status="active", @created_at="2013-07-04T15:39:49Z">]
~~~

All items in this array are valid Droplet objects, which responds to anything, that Droplet know (see below)

## Droplet

*Digital Ocean API equivalent: /droplets/[id]/*

~~~ruby
Oceanarium::droplet(droplet_id)
~~~

Returns a Droplet object with selected ID. Droplet is a Ruby object, which have some useful parameters.

~~~ruby
# valid droplet id
> Oceanarium::droplet(100500)
=> #<Oceanarium::Droplet:0x007fb29eaeaf80 @object={"id"=>100500, "name"=>"example.com", "image_id"=>1, "size_id"=>1, "region_id"=>1, "backups_active"=>nil, "ip_address"=>"192.0.2.1", "locked"=>false, "status"=>"active", "created_at"=>"2013-07-04T15:39:49Z"}, @id=100500, @name="example.com", @image_id=1, @size_id=1, @region_id=1, @backups_active=nil, @ip_address="192.0.2.1", @status="active", @created_at="2013-07-04T15:39:49Z">
# invalid droplet id
> Oceanarium::droplet(201000)
=> #<Oceanarium::Droplet:0x007fb29ea8ecf8 @object=nil, @id=nil>
~~~

### Droplet object parameters

* **id** — Returns an droplet ID:

         > s = Oceanarium::droplet(269383)
         => #<Oceanarium::Droplet:0x007fb29eb49760 ...>
         > s.id
         => 269383

* **name** — Returns droplet's name:


         > s = Oceanarium::droplet(269383)
         => #<Oceanarium::Droplet:0x007fb29eb49760 ...>
         > s.name
         => "example.com"