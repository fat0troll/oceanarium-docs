## Event

*Digital Ocean equivalent: /events/[event_id]*

~~~ruby
Oceanarium::event(event_id)
~~~

Returns an Event with selected ID. Event is an object which provides information about some process' status. You can retrieve it by event_id, which attached to long process API calls.

~~~ruby
# valid event id
> Oceanarium::event(100500)
=> #<Oceanarium::Event:0x007febb5aed320 @object={"action_status"=>nil, "droplet_id"=>302357, "event_type_id"=>4, "id"=>100500, "percentage"=>"3"}, @id=100500, @action_status=nil, @droplet_id=302357, @event_type_id=4, @percentage="3">
# invalid event id
> Oceanarium::event(201000)
=> #<Oceanarium::Event:0x007febb5abc860 @object=nil, @id=nil>
~~~

### Event object parameters

#### id

~~~ruby
> Oceanarium::event(100500).id
=> 100500
~~~

Returns an Event ID. Numeric.

#### action_status

~~~ruby
> Oceanarium::event(100500).action_status
=> "done"
~~~

Returns an Event status. May be nil or string.

#### droplet_id

~~~ruby
> Oceanarium::event(100500).droplet_id
=> 201000
~~~

Returns ID of Droplet which called this Event. Numeric

#### event_type_id

~~~ruby
> Oceanarium::event(100500).event_type_id
=> 1
~~~

Returns an Event type ID. Unfortunately, DigitalOcean help isn't described this value yet. Numeric.

#### percentage

~~~ruby
> Oceanarium::event(100500).percentage
=> "100"
~~~

Returns an Event progress. 100 is equivalent to "done".
