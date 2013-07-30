## List all SSH keys

*Digital Ocean equivalent: /ssh_keys/*

~~~ruby
> Oceanarium::ssh_keys
=> [#<Oceanarium::SSHKey:0x007f62bc59b408 @object={"id"=>24582, "name"=>"troller"}, @id=24582, @name="troller", @ssh_pub_key=nil>]
~~~

Returns an array of SSHKey objects. SSHKey is a (oh wow!) ssh key — for more information about SSH keys read manual [here](https://www.digitalocean.com/ssh_keys).

Beware: as of August 1, Digital Ocean in this command returns only key names, without key values. Parameter ssh_pub_key is nil here!

## SSHKey

*Digital Ocean equivalent: /ssh_keys/[ssh_key_id]*

~~~ruby
Oceanarium::ssh_key(ssh_key_id)
~~~

Returns an SSHKey object.

~~~ruby
# valid key id
> Oceanarium::ssh_key(24582)
=> #<Oceanarium::SSHKey:0x007f62bc5ffb10 @object={"id"=>24582, "name"=>"troller", "ssh_pub_key"=>[some key]}, @id=24582, @name="troller", @ssh_pub_key=[some key]>
# invalid key id
> Oceanarium::ssh_key(invalid_key_id)
=> #<Oceanarium::SSHKey:0x007f62bc631728 @object=nil, @id=nil>
~~~

### SSHKey object parameters

#### id

~~~ruby
> Oceanarium::ssh_key(24582).id
=> 24582
~~~

Returns a SSHKey id. Numeric.

#### name

~~~ruby
> Oceanarium::ssh_key(24582).name
=> "troller"
~~~

Returns a SSHKey name. String.

#### ssh_pub_key

~~~ruby
> Oceanarium::ssh_key(24582).ssh_pub_key
=> [some long string]
~~~

Returns a SSHKey value (ssh public key, which may be added to ~/.ssh/authorized_keys). String. Note: due to Digital Ocean restrictions, when you call *Oceanarium::ssh_keys*, all keys in array will have nil in ssh_pub_key parameter! If you want to get it, you must to get single key.

### Creating new SSH key

*Digital Ocean equivalent: /ssh_keys/new/?name=[ssh_key_name]&ssh_pub_key=[ssh_public_key]*

~~~ruby
Oceanarium::ssh_key.new(name, new_key)
~~~

Creating new SSH key on Digital Ocean. Returns SSHKey object.

~~~ruby
> Oceanarium::ssh_key.new("test", [some key])
=> #<Oceanarium::SSHKey:0x007fd337912190 @object={"id"=>26585, "name"=>"test", "ssh_pub_key"=>[some key]}, @id=26585, @name="test", @ssh_pub_key=[some key]>
~~~

#### Parameters

* **name** — new key's name. String.
* **new_key** — new SSH key. String. Must be valid SSH public key.

### Actions on SSH keys

#### edit

*Digital Ocean equivalent: /ssh_keys/[ssh_key_id]/edit/?ssh_key_pub=[ssh_public_key]*

~~~ruby
> Oceanarium::ssh_key(100500).edit(new_key)
=> #<Oceanarium::SSHKey:0x007fd337912190 @object={"id"=>100500, "name"=>"old name", "ssh_pub_key"=>[brand new key]}, @id=100500, @name="old name", @ssh_pub_key=[brand new key]>
~~~

This action will update your SSH key with the new one, passed in parameter. Returns nil if any error occurs.

Parameters:

* **new_key** — new SSH key. String. Must be valid SSH public key.

#### destroy

*Digital Ocean equivalent: /ssh_keys/[ssh_key_id]/destroy/*

~~~ruby
> Oceanarium::ssh_key(100500).destroy
=> "OK"
~~~

Destroying SSH key. This operation cannot be undone. Unlike droplets, there is no SSH key "archive". Returns "OK" if all OK, else — "Error" or "ERROR".