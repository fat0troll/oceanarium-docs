## List all sizes

*Digital Ocean equivalent: /sizes/*

~~~ruby
> Oceanarium::sizes
=> [#<Oceanarium::Size:0x007fd337cde1c0 @object={"id"=>66, "name"=>"512MB", "slug"=>nil}, @id=66, @name="512MB">, #<Oceanarium::Size:0x007fd337cde148 @object={"id"=>63, "name"=>"1GB", "slug"=>nil}, @id=63, @name="1GB">, #<Oceanarium::Size:0x007fd337cde0d0 @object={"id"=>62, "name"=>"2GB", "slug"=>nil}, @id=62, @name="2GB">, #<Oceanarium::Size:0x007fd337cde058 @object={"id"=>64, "name"=>"4GB", "slug"=>nil}, @id=64, @name="4GB"> … ] # and so on
~~~

Returns an Array with Size objects. Size is a perfomance setting — it have visible parameter (RAM size), and invisible parameters, connected to RAM size — HDD size, and processor's perfomance. Bigger RAM will bring you bigger HDD and faster CPU.

## Size

There is no method to get one Size by ID. There is no reason to do it.

### Size object parameters

#### id

Returns a Size ID. Numeric.

#### name

Returns a RAM size, provided by this Size. String.