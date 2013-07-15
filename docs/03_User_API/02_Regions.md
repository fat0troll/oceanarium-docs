## List all regions

*Digital Ocean equivalent: /regions/*

~~~ruby
> Oceanarium::regions
=> [#<Oceanarium::Region:0x007f4f6a9b6a48 @object={"id"=>1, "name"=>"New York 1", "slug"=>"nyc1"}, @id=1, @name="New York 1", @slug="nyc1">, #<Oceanarium::Region:0x007f4f6a9b69a8 @object={"id"=>2, "name"=>"Amsterdam 1", "slug"=>"ams1"}, @id=2, @name="Amsterdam 1", @slug="ams1">, #<Oceanarium::Region:0x007f4f6a9b6908 @object={"id"=>3, "name"=>"San Francisco 1", "slug"=>"sfo1"}, @id=3, @name="San Francisco 1", @slug="sfo1">]
~~~

Returns an array of Region objects. Region is a datacenter area, used, for example, in droplet creation.

## Region

There is no method to get one region by ID. There is no reason to do it.

### Region object parameters

#### id

Returns region ID. Numeric.

#### name

Returns region name. String.

#### slug

Returns region slug (shortcut). String without spaces.
