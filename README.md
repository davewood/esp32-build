# Build ESP32 firmware with Docker

## Getting Started
```
mkdir micropython-esp32
cd micropython-esp32
```

## Clone micropython repository
```
git clone https://github.com/micropython/micropython
```

## Clone this repository
`git clone https://github.com/davewood/esp32-build`

## Build docker image
```
cd esp32-build
docker build -t esp32-build .
cd ..
```

## Build micropython
```
docker run \
  --mount src="`pwd`/micropython",target=/tmp/micropython,type=bind esp32-build \
  bash -c 'cd /tmp/micropython/mpy-cross && make && \
           cd /tmp/micropython/ports/esp32 && idf.py build'
```
