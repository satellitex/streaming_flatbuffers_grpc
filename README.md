# Grpc + flatbuffers + Streaming Connection test ( alike Sync )

## prepare
```
cd docker
docker build -t satellitex/flatbuf-test .
docker run -it --name flat-test -v streaming_flatbuffers_grpc:/opt/flat-test satellitex/flatbuf-test /bin/bash
```


## build
```
mkdir buid
cd build
cmake ..
make
```