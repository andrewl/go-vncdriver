`Dockerfile` defines a tiny docker image that contains only the `transcode`
executable. The resulting image is about 6MB.

`transcode` is a statically-linked Linux executable:

```
$ file transcode
transcode: ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, for GNU/Linux 2.6.24, not stripped
```

Built on Linux using:

```
GOPATH=/Users/jgray/openai/ go build --ldflags '-extldflags "-static"' main.go
```

Use the image like so:

```
docker run -v volume:mount docker.openai.com/transcode -in=server.tight.fbs -out=server.raw.fbs
```
