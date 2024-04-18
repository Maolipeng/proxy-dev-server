# @maolipeng/proxy-dev-server

这是一个简单的代理服务器，它可以处理HTTP和HTTPS请求，并将这些请求代理到目标服务器。有这样一个场景，在开发环境下，我们的请求有些是通过重定向的，在本地开发环境下就会出现cors错误，还有一些老项目直接访问不通域的接口，也会出现cors错误，为了解决这个问题，我们可以使用这个代理服务器。这样不改变后端的安全配置就能解决问题
## Install

```bash
$ pnpm i -D @maolipeng/proxy-dev-server
```

## Usage
可以在命令行中使用my-proxy-server命令来启动这个服务器。需要提供一些选项，如目标服务器的URL、监听的端口和主机名等。以下是一个示例：
```bash
proxy-server --target http://example.com --port 8000 --hostname localhost

```
这将会启动一个监听localhost的8000端口的HTTP代理服务器，所有的请求都会被代理到http://example.com。
### https
如果你需要HTTPS，你可以提供--https、--key和--cert选项，如下所示：
```bash
my-proxy-server --target http://example.com --port 8000 --hostname localhost --https ./key.pem --cert ./cert.pem

```
这将会启动一个监听localhost的8000端口的HTTPS代理服务器，所有的请求都会被代理到http://example.com。请注意，你需要将./key.pem和./cert.pem替换为你的HTTPS证书的实际路径。

### 配置文件
你也可以使用一个.proxyrc.js文件来配置你的服务器。这个文件应该导出一个对象，这个对象包含了你的配置选项。例如：
```js
module.exports = {
    target: 'http://example.com',
    port: 8000,
    hostname: 'localhost',
    https: false,
};

```
然后，你可以使用以下命令来启动你的服务器：
```bash
proxy-server
```
这将会使用.proxyrc.js文件中的配置选项来启动你的服务器。如果你想覆盖配置文件中的某些选项，你可以提供命令行参数。

## LICENSE

MIT
