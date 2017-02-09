## The function
A function has an input, does stuff and produces an output.

Using this definition, many things are functions. Dogs eat food, 
play fetch and poop on the floor. Cars take people as input, drive to
the store and produce people as an output. Your computer received a
mouse click or a screen tap as an input, fetched this page and is now
displaying it to you.

A pure function is one that uses only its input to produce its output.
This make accounting for what the function does (and importantly, *did*)
much easier.

A function can also "close over" variables.

```javascript
var makeCounter = function(){
    var counter = 0;
    
    return {
        increment: function() {
            counter = counter + 1
        },
        value: function() {
            return counter;
        }
    }
};
```

In the above code, `counter` is "closed over" in the "closure" of 
`makeCounter`. `counter` shouldn't be directly accessed outside
of `makeCounter` but the functions `increment` and `value` can access it
and they can be used outside `makeCounter`. By using the closure, the
programmer can save data and set up specific ways to access it.

## The List

## The Associative Array
Also known by "map", "dictionary", "table", "hash".

The associative array store value(s) with useful addresses, called a key. 
Given an assoc. array and a key, you can `get` or `put` data at that key.
 
Mailboxes at an apartment complex are like an associative array. The "key"
is the meaningless number on the front. The mail carrier knows how to map
the number on the front to street addresses and `put` the letters
and catalogs into the correct boxes. Later, you `get` the mail.

The contacts app in your phone is like an assoc. array. The keys are
names and the values on that key are the phone number, email address,
profile picture, etc.

In computering, DNS is like a distributed assoc. array. The key is the
hostname like `example.com` and the value is something like `1.2.3.4`.
In reality it's slightly more complicated with `A` records and `CNAMES`
but that's another article for another time. If your computer doesn't
have the value for `example.com`, it asks your router. If your router
doesn't have the value, it asks your ISP. If your ISP doesn't have the
value, it asks one of it's friends. And so on, until a root DNS server
is reached which has the value or *the hostname doesn't exist*.

## Mapping an array

## Filtering an array

## Reducing an array
Also known by "fold"

###### Additional Reading
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures