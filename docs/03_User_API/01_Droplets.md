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

#### id

Returns an droplet ID:

~~~ruby
> s = Oceanarium::droplet(100500)
=> #<Oceanarium::Droplet:0x007fb29eb49760 ...>
> s.id
=> 100500
~~~

#### name

Returns droplet's name:

~~~ruby
> s = Oceanarium::droplet(100500)
=> #<Oceanarium::Droplet:0x007fb29eb49760 ...>
> s.name
=> "example.com"
~~~

#### image_id

Returns droplet's image ID. Image is an disk snapshot (with system or user data).

~~~ruby
> s = Oceanarium::droplet(100500)
=> #<Oceanarium::Droplet:0x007fb29eb49760 ...>
> s.image_id
=> 1
~~~

#### size_id

Returns droplet's size ID. Size is a droplet's perfomance parameter — droplets RAM and processor in Digital Ocean depends on droplet's size.

~~~ruby
> s = Oceanarium::droplet(100500)
=> #<Oceanarium::Droplet:0x007fb29eb49760 ...>
> s.size_id
=> 1
~~~

#### region_id

Returns droplet's region ID. Region is a datacenter, where hosted your Droplet.

~~~ruby
> s = Oceanarium::droplet(100500)
=> #<Oceanarium::Droplet:0x007fb29eb49760 ...>
> s.region_id
=> 1
~~~

#### backups_active

Indicates if backups are active for this droplet.

~~~ruby
> s = Oceanarium::droplet(100500)
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
~~~

#### ip_address

Returns droplet's IP address.

~~~ruby
> s = Oceanarium::droplet(100500)
=> #<Oceanarium::Droplet:0x007fb29eb49760 ...>
> s.ip_address
=> "192.0.2.1"
~~~

#### status

Returns droplet's status. May be *"new"*, *"active"*, *"off"*, *"archive"*

~~~ruby
> s = Oceanarium::droplet(100500)
=> #<Oceanarium::Droplet:0x007fb29eb49760 ...>
> s.status
=> "active"
~~~

#### created_at

Returns creation time. Isn't Ruby-friendly yet.

~~~ruby
> s = Oceanarium::droplet(100500)
=> #<Oceanarium::Droplet:0x007fb29eb49760 ...>
> s.created_at
=> "2013-07-04T15:39:49Z"
~~~

### Creating new droplet

~~~ruby
Oceanarium::droplet.new(name, size_id, image_id, region_id[, ssh_key_ids])
~~~

*Digital Ocean equivalent: /droplets/new?name=[droplet_name]&size_id=[size_id]&image_id=[image_id]&region_id=[region_id]&ssh_key_ids=[ssh_key_id1],[ssh_key_id2]*

Creating new Droplet on Digital Ocean with selected parameters. Returns new droplet ID and event ID (for more informations see Events article).

~~~ruby
# valid parameters
> Oceanarium::droplet.new('example.com', 1, 1, 1)
=> ["100500", 201000]
# invalid parameters, droplet is not created
> Oceanarium::droplet.new('example.com', 'broken', 1, 1)
=> nil
~~~

#### Parameters

* **name** — new droplet's name. String. Must be fully qualified domain name.
* **size_id** — droplet's size ID. Numeric. For getting avaliable sizes, see Sizes article of the documentation.
* **image_id** — droplet's image ID. Numeric. For getting avaliable images, see Images article of the documentation.
* **region_id** — droplet's region ID. Numeric. For getting avaliable regions, see Regions article of the documentation.

#### Optional parameters

* **ssh_key_ids** — SSH keys, which will be uploaded to droplet on creation. From Digital Ocean's help:

        You can add SSH keys to DigitalOcean which can then be selected during the droplet create process to add the selected SSH keys under the root user.

This parameter is a comma-separated string with key IDs. For getting avaliable keys, see SSH Keys article of the documentation.

### Actions on droplet

#### Reboot

*Digital Ocean equivalent: /droplets/[droplet_id]/reboot/*

~~~ruby
> Oceanarium::droplet(100500).reboot
=> ["OK", 201000]
~~~

Reboot selected Droplet. Returns "OK" and event ID if success, else — "ERROR" or "Error".

#### Power cycle

*Digital Ocean equivalent: /droplets/[droplet_id]/power_cycle/*

~~~ruby
> Oceanarium::droplet(100500).reboot
=> ["OK", 201000]
~~~

Power cycle selected Droplet. Returns "OK" and event ID if success, else — "ERROR" or "Error".

#### Shut down

*Digital Ocean equivalent: /droplets/[droplet_id]/shutdown/*

~~~ruby
> Oceanarium::droplet(100500).shutdown
=> ["OK", 201000]
~~~

Shut down selected Droplet. Returns "OK" and event ID if success, else — "ERROR" or "Error".

#### Power off

*Digital Ocean equivalent: /droplets/[droplet_id]/power_off/*

~~~ruby
> Oceanarium::droplet(100500).power_off
=> ["OK", 200100]
~~~

Power off selected Droplet. Returns "OK" and event ID if success, else — "ERROR" or "Error".

#### Power on

*Digital Ocean equivalent: /droplets/[droplet_id]/power_on/*

~~~ruby
> Oceanarium::droplet(100500).power_on
=> ["OK", 201000]
~~~

Power on selected Droplet. Returns "OK" and event ID if success, else — "ERROR" or "Error".

#### Password reset

*Digital Ocean equivalent: /droplets/[droplet_id]/password_reset/*

~~~ruby
> Oceanarium::droplet(100500).password_reset
=> ["OK", 200100]
~~~

Reset root password on selected Droplet. Returns "OK" and event ID if success, else — "ERROR" or "Error". Droplet will be rebooted while resetting. Note: password will be sent to Digital Ocean user's e-mail.

#### Resize

*Digital Ocean equivalent: /droplets/[droplet_id]/resize/?size_id=[size_id]*

~~~ruby
> Oceanarium::droplets(100500).resize(size_id)
=> ["OK", 201000]
~~~

Doing resize on a selected Droplet. This will also affect the number of processors and memory allocated to the droplet.

Parameters:

* **size_id** — New size ID. Numeric. For getting avaliable sizes, see Sizes article of the documentation.

#### Snapshot

*Digital Ocean equivalent: /droplets/[droplet_id]/snapshot/?name=[snapshot_name]*

~~~ruby
> Oceanarium::droplet(100500).snapshot(snapshot_name)
=> ["OK", 201000]
~~~

Takes snapshot of current droplet state. May cause droplet reboot.

Parameters:

* **snapshot_name** — Name of the new snapshot. String.

#### Restore

*Digital Ocean equivalent: /droplets/[droplet_id]/restore/?image_id=[image_id]*

~~~ruby
> Oceanarium::droplet(100500).restore(image_id)
=> ["OK", 201000]
~~~

Restore selected image to droplet. Make sure that you have backups of all important information first.

Parameters:

* **image_id** — selected image ID. For getting avaliable images see Images article of the documentation.

#### Rebuild

*Digital Ocean equivalent: /droplets/[droplet_id]/rebuild/?image_id=[image_id]*

~~~ruby
> Oceanarium::droplet(100500).restore(image_id)
=> ["OK", 201000]
~~~

Rebuild droplet from scratch with selected image. Useful when you need to start over, but with same IP.

Parameters:

* **image_id** — selected image ID. For getting avaliable images see Images article of the documentation.

#### Backups

##### Enable backups

*Digital Ocean equivalent: /droplets/[droplet_id]/enable_backups/*

~~~ruby
> Oceanarium::droplet(100500).enable_backups
=> ["OK", 201000]
~~~

Enables automatic backups which run in the background daily to backup your droplet's data. Returns "OK" and event ID if success, else — "ERROR" or "Error".

##### Disable backups

*Digital Ocean equivalent: /droplets/[droplet_id]/disable_backups/*

~~~ruby
> Oceanarium::droplet(100500).disable_backups
=> ["OK", 201000]
~~~

Disables backups on selected droplet.

#### Rename

*Digital Ocean equivalent: /droplets/[droplet_id]/rename/?name=[name]*

~~~ruby
> Oceanarium::droplet(100500).rename(name)
=> ["OK", 201000]
~~~

Renames droplet to new name. Name must be fully qualified domain name.

Parameters:

* **name** — New droplet's name. String.

#### Destroy

*Digital Ocean equivalent: /droplets/[droplet_id]/destroy/*

~~~ruby
> Oceanarium::droplet(100500).destroy
=> ["OK", 201000]
~~~

Just kill the cat. Destroying droplet, now it's in archive.
