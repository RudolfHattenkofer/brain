```swift
set -x CFLAGS -I(brew --prefix openssl)/include -I(brew --prefix bzip2)/include -I(brew --prefix readline)/include -I(xcrun --show-sdk-path)/usr/include
set -x LDFLAGS -L(brew --prefix openssl)/lib -L(brew --prefix readline)/lib -L(brew --prefix zlib)/lib -L(brew --prefix bzip2)/lib
pyenv install
```

Install GRPCIO [Ticket](https://github.com/grpc/grpc/issues/24677) [Ticket](https://github.com/grpc/grpc/issues/24248) Ticket

```swift
pipenv shell
set -x GRPC_BUILD_WITH_BORING_SSL_ASM ""
set -x GRPC_PYTHON_BUILD_SYSTEM_RE2 true
set -x GRPC_PYTHON_BUILD_SYSTEM_OPENSSL true
set -x GRPC_PYTHON_BUILD_SYSTEM_ZLIB true

# THIS IS IT!
set -x SYSTEM_VERSION_COMPAT 1

pip install grpcio
```



