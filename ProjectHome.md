CityHash provides hash functions for strings. It has been superseded by [FarmHash](https://code.google.com/p/farmhash/). Further updates to CityHash are fairly unlikely.

The latest stable version of CityHash is [cityhash-1.1.1.tar.gz](http://code.google.com/p/cityhash/downloads/detail?name=cityhash-1.1.1.tar.gz&can=2&q=). Differences between versions are explained in the [NEWS](http://code.google.com/p/cityhash/source/browse/trunk/NEWS) file.

The functions mix the input bits thoroughly but are not suitable for cryptography. We provide reference implementations in C++, with a friendly MIT license.  The code's portable; let us know if you encounter problems. To download the code use the .tar.gz file or use svn with [these instructions](https://code.google.com/p/cityhash/source/checkout).

The [README](http://code.google.com/p/cityhash/source/browse/trunk/README) contains a good explanation of the various CityHash functions. However, here is a short summary:

CityHash64() and similar return a 64-bit hash.  Inside Google, where CityHash was developed starting in 2010, we use variants of CityHash64() mainly in hash tables such as hash\_map<string, int>.

CityHash32() returns a 32-bit hash.  It's mostly useful in 32-bit code (e.g., x86).

CityHash128() and similar return a 128-bit hash and are tuned for strings of at least a few hundred bytes. Depending on your compiler and hardware, it may be faster than CityHash64() on sufficiently long strings. It is known to be slower than necessary on shorter strings, but we expect that case to be relatively unimportant. Inside Google we use variants of CityHash128() mainly for code that wants to minimize collisions.

CityHashCrc128() and CityHashCrc256() and similar are additional variants, specially tuned for CPUs with SSE4.2.