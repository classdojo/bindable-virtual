```coffeescript
bindable = require "bindable"
virtual  = require "bindable-virtual"


class Person extends bindable.Object

  ###
  ###
  
  constructor: (first, last) ->
    super { first: name, last: last }
    
    virtual @, "friends", get: @getFriends
    
  ###
  ###
  
  getFriends: (next) =>
    loadFriends @, next


person = new Person("craig", "condon")

# undefined
console.log person.get "friends"

# triggers virtual field
person.bind "friends", (friends) ->

# bind to friends friends
person.bind "friends.@each.friends.@each.first", (firstNames) ->  
  
  


```
