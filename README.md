unigornel
=========

[![Build Status](https://jenkins.unigornel.org/buildStatus/icon?job=unigornel-master)](https://jenkins.unigornel.org/job/unigornel-master/)

This software is in development phase.

About
-----

Unigornel is a library operating system written in Go. It compiles Go code to
unikernels that run under the Xen hypervisor.

Installation
------------

We assume
  - `/usr/local/go` holds a recent version of Go.
  - `$GOPATH/bin` is present in your `$PATH`

```
go get -v github.com/unigornel/unigornel/unigornel
cd $GOPATH/src/github.com/unigornel
git submodule update --init --recursive
GOROOT_BOOTSTRAP=/usr/local/go make
make install
```

Setup the unigornel environment
-------------------------------

The installation procedure installs the `unigornel` binary in `$GOPATH/bin`.
This binary is used to setup the environment and compile unikernels.

```
eval $(unikernel env)
cd $GOPATH/src/your-unikernel
unikernel build -o your-unikernel
```

Testing
-------

To run the tests, you need a working Xen installation. You should run the
`integration_tests` binary as root, as it needs to launch Xen domains.

```
go get -v github.com/unigornel/unigornel/integration_tests
cd $GOPATH/src/github.com/unigornel/integration_tests
go build
./integration_tests -h
```
