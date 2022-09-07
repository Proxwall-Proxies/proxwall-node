<p align="center"><img src="https://github.com/Proxwall-Proxies/paid-proxy-server/raw/master/uv.png" height="200">
</p>

<h1 align="center">ProxWall-Node</h1>

<p align="center">The deployable version of ProxWall, a highly sophisticated proxy used for evading internet censorship or accessing websites in a controlled sandbox using the power of service-workers and more!<br><br></p>

## Features
- CAPTCHA support along with hCAPTCHA support
- URL encoding settings to further hide activity when using ProxWall
- Configuration all done on the client-side via service-workers
- Speed in comparison to other web proxies that fully proxy content
- Blacklist setting and more for easy hosting
- Security in mind and leak prevention
- Frequent updates to improve site support or fix security issues

## Supported Sites
- [Youtube](https://www.youtube.com)
- [CAPTCHA/hCAPTCHA](https://www.captcha.net)
- [Spotify](https://spotify.com)
- [Discord](https://discord.com)
- [Reddit](https://reddit.com)
- [GeForce NOW](https://play.geforcenow.com/) (Partially Supported)
- And more!

## Technologies Used
- Service Workers
- HTML, JS, CSS rewriting
- Parse5
- Acorn.js

# Installation and Setup

Installation of ProxWall is simple. You can find a Tl;DR of the installation and setup process just below. If you are unfamiliar with the "standard" installation process, look a bit farther down for a more comprehensive installation and setup guide.

## Basic Guide

```sh
$ git clone https://github.com/Proxwall-Proxies/paid-proxy-server.git --recursive
$ cd paid-proxy-server
$ npm install
$ npm start
```

## Comprehensive Guide

Below will describe a comprehensive guide to install ProxWall on Linux machines.

To clone the repository, simply run the following command:

```sh
$ git clone https://github.com/titaniumnetwork-dev/paid-proxy-server --recursive
```

The `--recursive` flag will clone the repository and all submodules.

To begin work on the actual setup, cd into the repository. You can do so by running the following command:

```sh
$ cd paid-proxy-server
```

From here, you can update your submodules and install your dependencies. To do so, run the following command:

```sh
$ npm install
```

Finally, to start ProxWall, run the following command:

```sh
$ npm start
```

You can then find ProxWall on `http://127.0.0.1:8080`. If you would like to change the port UV will be running on, edit the last line in `index.mjs`. 

Please note that UV will not function without HTTPS. If you are hosting on Replit or Heroku, this won't be a problem as they provide you with SSL/TLS by default and will automatically apply it to your instance, however if you are attempting to host UV on a different platform, such as a personal server, you **WILL** need to use HTTPS. 

## Configuration
Configuring ProxWall is very simple. Simple descriptions of each configurable option are provided as a comment in the block below. More detailed documentation can be found just below mentioned block.

`uv.config.js`

```javascript
self.__uv$config = {
    prefix: '/sw/', // Proxy url prefix
    bare: '/bare/', // Bare server location
    encodeUrl: ProxWall.codec.xor.encode, // URL Encoding function
    decodeUrl: ProxWall.codec.xor.decode, // Decode URL function
    handler: '/uv.handler.js', // Handler script
    bundle: '/uv.bundle.js', // Bundled script
    config: '/uv.config.js', // Configuration script
    sw: '/uv.sw.js', // Service Worker Script
};
```

| Configuration | Options and Explanation |
| ------------- | ----------------------- |
| Prefix | The prefix is the prefix that you want users to see. Ex: `https://example.com/service.` The default prefix is `service`. |
| Bare | Bare Servers can run on directories. For example, if the directory was /bare/ then the bare origin would look like `http://example.org/bare/`. The bare origin is passed to clients. |
| encodeUrl| EncodeUrl is how you want the URL a proxy site's visitors has to be encoded. Options include `ProxWall.codec.base64.encode`, `ProxWall.codec.plain.encode`, or `ProxWall.codec.xor.encode`. It is recommended that you use `xor` or `base64` as it hides the queries your visitors are searching and visiting.
| decodeURL | DecodeUrl is how you want the url to be decoded. It is recommended you keep it the same as `encodeUrl`. |
| Handler | Handler is the path to the UV handler. The default name and path to this file is `static/uv/uv.handler.js`. |
| Bundle | Bundle is the path to the UV bundle file. The default name and path to this file is `static/uv/uv.bundle.js`. |
| Config | Config is the path to the UV config file. The default name and path to this file is `static/uv/uv.bundle.js`. |
| SW | SW is the path to the UV Service Worker script. The default name and path to this file is `static/uv/uv.sw.js`. |

## Static Files

Static files is the frontend for ProxWall.