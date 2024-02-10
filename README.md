# Scan all images in a kubernetes namespace with Neuvector

A simple script that calls `docker run neuvector/scanner:latest` with all images
in a kubernetes namespace.

## Installation

You must have docker installed. To get running images in a namespace, you must
be connected to the kubernetes cluster and have access to that namespace. Ensure
you can list the pods with this command:

```sh
kubectl get pods -n <namespace>
```

## Usage

Scan all images in namespace `my-namespace`:

```sh
./scan my-namespace
```

Scan an individual image uploaded to some registry (you don't need this repo for
this)

```sh
docker run neuvector/scanner:latest busybox:latest
```

## TODO

I couldn't get neuvector/scanner to scan a local image. It's supposed to be
possible using their [github action](https://github.com/neuvector/scan-action).
I tried building the [code](https://github.com/neuvector/scanner) that the
action uses but got the following errors. Perhaps a Mac issue?

```
package github.com/neuvector/scanner
        imports github.com/neuvector/neuvector/share/cluster
        imports github.com/neuvector/neuvector/share/osutil: build constraints exclude all Go files in /Users/arvbju01/projects/scanner/vendor/github.com/neuvector/neuvector/share/osutil
package github.com/neuvector/scanner
        imports github.com/neuvector/neuvector/share/global
        imports github.com/neuvector/neuvector/share/orchestration
        imports github.com/neuvector/neuvector/share/system/sidekick: build constraints exclude all Go files in /Users/arvbju01/projects/scanner/vendor/github.com/neuvector/neuvector/share/system/sidekick
```
