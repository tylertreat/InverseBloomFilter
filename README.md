# Inverse Bloom Filter

An inverse Bloom filter, or "the opposite of a Bloom filter", is a concurrent, probabilistic data structure used to test whether an item has been observed or not. This is a Go implementation, [originally by Jeff Hodges](http://www.somethingsimilar.com/2012/05/21/the-opposite-of-a-bloom-filter/), which replaces the use of MD5 hashing with a non-cryptographic FNV-1a function.

The inverse filter may report a false negative but can never report a false positive. That is, it may report that an
item has not been seen when it actually has, but it will never report an item as seen which it hasn't come across. This behaves in a similar manner to a fixed-size hashmap which does not handle conflicts.

An example use case is de-duplicating events while processing a stream of data. Ideally, duplicate events are relatively close together.
