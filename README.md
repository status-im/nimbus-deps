# nimbus-deps
Nimbus binary dependencies

# Installation
To build `nimbus-deps` manually you need to have Microsoft Visual Studio 2017 installed.

Please follow this steps to build Snappy and RocksDB DLLs.

```shell
# Installing `vcpkg`.
git clone https://github.com/Microsoft/vcpkg.git
cd vcpkg
.\bootstrap-vcpkg.bat
cd ..

# Installing `nimbus-deps`.
git clone https://github.com/status-im/nimbus-deps.git
# Copy `nimbus-deps` triplets files to `vcpkg` triplets directory
copy nimbus-deps\triplets\*.* vcpkg\triplets\

# Building packages
cd vcpkg
# Build x86 standalone DLL for snappy library.
vcpkg install snappy:x86-windows-static-crt
# Build x64 standalone DLL for snappy library.
vcpkg install snappy:x64-windows-static-crt
# Build x86 standalone DLL for rocksdb library.
vcpkg install rocksdb[lz4,snappy,zlib]:x86-windows-rocksdb
# Build x64 standalone DLL for rocksdb library
vcpkg install rocksdb[lz4,snappy,zlib]:x64-windows-rocksdb
```

After successfull build you can find your dlls:

```shell
# Snappy x86
vcpkg\installed\x86-windows-static-crt\bin\snappy.dll
# Snappy x64
vcpkg\installed\x64-windows-static-crt\bin\snappy.dll
# RocksDB x86
vcpkg\installed\x86-windows-rocksdb\bin\rocksdb-shared.dll
# RocksDB x64
vcpkg\installed\x64-windows-rocksdb\bin\rocksdb-shared.dll
```

