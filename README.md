# proxylocal
[![gorelease](https://dn-gorelease.qbox.me/gorelease-download-blue.svg)](http://gorelease.herokuapp.com/codeskyblue/proxylocal)

Proxy local service to public.

> I want to expose a local server behide a NAT or firewall to the internet.

There are some similar service.

* <https://ngrok.com/>
* <http://www.tunnel.mobi/> Use ngrok, VPS in china.
* <https://forwardhq.com/> Need pay price to get service.

At the beginning this is just for study how to proxy local server to public network. Now it can be stable use.

这个东西目前看来确实是个很不错的东西，可以调试微信，可以把自家路由器的东西放到外网。还可以通过它的tcp转发功能，远程调试家中的树莓派。用途多多

不过服务器需要自己搭

## Installation
Build from source code

```
go get -v github.com/codeskyblue/proxylocal
```

<del>Or [download](https://github.com/codeskyblue/proxylocal/releases) according to your platform.</del>

## Usage
Run server in a public network, listen in port 8080 (Assuming your ip is 122.2.2.1)

	proxylocal --listen 8080

Assume you are running your local tcp-server on port 5037. To make it publicly available run:

	proxylocal --server 122.2.2.1:8080 --proto tcp 5037

If this is a web server, only need to update `--proto`
	
	proxylocal --server 122.2.2.1:8080 --proto http 5037

	# expects output
	proxy URL: http://localhost:5037
	Recv Message: Local server is now publicly available via:
	http://wn8yn.t.localhost


### Environment
Server address default from env-var `PXL_SERVER_ADDR`

## LICENSE
MIT(LICENSE)
