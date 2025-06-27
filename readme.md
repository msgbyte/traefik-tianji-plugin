Fork from [traefik-umami-plugin](https://github.com/1cedsoda/traefik-umami-plugin)


# Installation
To [add this plugin to traefik](https://plugins.traefik.io/install) reference this repository as a plugin in the static config.
The version references a git tag.

```yaml
experimental:
  plugins:
    traefik-tianji-plugin:
      moduleName: "github.com/msgbyte/traefik-tianji-plugin"
      version: "v1.0.0" 
```
```toml
[experimental.plugins.traefik-tianji-plugin]
  moduleName = "github.com/msgbyte/traefik-tianji-plugin"
  version = "v1.0.0"
```
With the plugin installed, you can configure a middleware in a dynamic configuration such as a `config.yml` or docker labels.
Inside `traefik-tianji-plugin` the plugin can be configured.

Only `tianjiHost` and `websiteId` options are required to get started.
The middleware can then be used in a [router](https://doc.traefik.io/traefik/routing/routers/#middlewares_1). Remember to reference the correct [provider namespace](https://doc.traefik.io/traefik/providers/overview/#provider-namespace).


```yaml
http:
  middlewares:
    my-tianji-middleware:
      plugin:
        traefik-tianji-plugin:
          tianjiHost: "https://app-tianji.msgbyte.com"
          websiteId: "<your-website-id>"
```
```toml
[http.middlewares]
  [http.middlewares.tianji.plugin.traefik-tianji-plugin]
    tianjiHost = "https://app-tianji.msgbyte.com"
    websiteId = "<your-website-id>"
```
