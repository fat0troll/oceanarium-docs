Oceanarium provides two API levels for application developers.

## User API

~~~ruby
Oceanarium::droplets
Oceanarium::droplet(100500).reboot
Oceanarium::ssh_key.new('test_key', the_key)
# and so on
~~~

User API — dedicated to gem's end users, follow the structure of current Digital Ocean API.

This API is stable. Any change in this API will affect major number of gem's version. So, in this release cycle (0.1.x, 0.2.x, and so on) you may be sure — User API the same, and isn't changed. If it will be changed, version 1.0.0 will be released.

We recommend you to use User API in your applications, because it's stable, but if you want to take the power to your hands...

## Core API

~~~ruby
Oceanarium::Droplet.all
Oceanarium::Droplet.find(100500)
Oceanarium::Image.find_by_name('ololo')
Oceanarium::SSHKey.new('test', the_key)
# and so on
~~~

Core API — collection of wrappers around Digital Ocean API. It's widely used by this gem (User API is just a shortcuts to Core API), and can be used by application developers too.

**WARNING: Core API is unstable. No one guarantees that in next version it's behaviour will be the same. We strongly recommends you to use User API instead!**

It may be changed in any minor or patch release — if Digital Ocean updates their API, Core API updates too as soon as possible. Core API changes will not affect User API in current release cycle, as described above.
