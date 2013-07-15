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

* **image_id** — Returns droplet's image ID. Image is an disk snapshot (with system or user data).

         > s = Oceanarium::droplet(269383)
         => #<Oceanarium::Droplet:0x007fb29eb49760 ...>
         > s.image_id
         => 1

* **size_id** — Returns droplet's size ID. Size is a droplet's perfomance parameter — droplets RAM and processor in Digital Ocean depends on droplet's size.

         > s = Oceanarium::droplet(269383)
         => #<Oceanarium::Droplet:0x007fb29eb49760 ...>
         > s.size_id
         => 1

* **region_id — Returns droplet's region ID. Region is a datacenter, where hosted your Droplet.

         > s = Oceanarium::droplet(269383)
         => #<Oceanarium::Droplet:0x007fb29eb49760 ...>
         > s.region_id
         => 1

* **backups_active** — Indicates if backups are active for this droplet.

         > s = Oceanarium::droplet(269383)
         => #<Oceanarium::Droplet:0x007fb29eb49760 ...>
         # backups setup isn't performed yet for this droplet
         > s.backups_active
         => nil
         # backups enabled
         > s.backups_active
         => true
         # backups disabled
         > s.backups_active
         => false

* **ip_address** — Returns droplet's IP address.

         > s = Oceanarium::droplet(269383)
         => #<Oceanarium::Droplet:0x007fb29eb49760 ...>
         > s.ip_address
         => "192.0.2.1"

* **status** — Returns droplet's status. May be *"new"*, *"active"*, *"off"*, *"archive"*

         > s = Oceanarium::droplet(269383)
         => #<Oceanarium::Droplet:0x007fb29eb49760 ...>
         > s.status
         => "active"

* **created_at** — Returns creation time. Isn't Ruby-friendly yet.

         > s = Oceanarium::droplet(269383)
         => #<Oceanarium::Droplet:0x007fb29eb49760 ...>
         > s.created_at
         => "2013-07-04T15:39:49Z"