# NOTE

This repo is for use by Identity while we transition legacy login flows onto our new SSO platform. This fork will be deleted when Identity no longer needs to maintain the legacy PHP-generated `prodigyweb` cookie.

Please don't consume this repo or commit any new code to it unless aboslutely necessary, and if you do please let us know in `#identity` on Slack.


# Ruby PHP Serializer

This module provides two methods: `PHP.serialize` and `PHP.unserialize`,
both of which should be compatible with the similarly named functions in PHP.

## Installing

In your `Gemfile`:
```ruby
gem "php-serialize"
```

## Usage

```ruby
PHP.serialize({'foo' => 'bar'})               #=> "a:1:{s:3:\"foo\";s:3:\"bar\";}"
PHP.unserialize('a:1:{s:3:"foo";s:3:"bar";}') #=> {"foo"=>"bar"}
```

`PHP.unserialize` can also read PHP sessions, which are collections of named
serialized objects.  These can be reserialized using `PHP.serialize_session`,
which has the same semantics as `PHP.serialize`, but which only supports Hash
and associative Arrays for the root object.

See http://php.net/serialize and http://php.net/unserialize for
details on the PHP side of all this.

## Acknowledgements

- TJ Vanderpoel, initial PHP serialized session support.
- Philip Hallstrom, fix for self-generated Structs on unserialization.
- Edward Speyer, fix for assoc serialization in nested structures.

Author: Thomas Hurst <tom@hur.st>, http://hur.st/
