# mailcow dockerless

My notes and patches to be able to run mailcow without a dependency on Docker.


- The database configuration allows access only via the socket. This means that remote databases cannot be used.
- Many file paths are hardcoded, although this would not be necessary.
- Excessive use of environment variables.<br>These are not accessed uniformly.
- The use of PECL extensions forces to build them from the source code.

