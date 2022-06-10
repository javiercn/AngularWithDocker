# AngularWithDocker

This repo demonstrates the steps to integrate an angular in an ASP.NET host running in docker. When running in development, the flow is as follows:

```mermaid
flowchart LR
  Browser -- "Connects to" -->AngularDevServer
  subgraph Host
    AngularDevServer["Angular Dev Server"]
  end
  AngularDevServer -- "Proxies requests to backend" --> Container
  subgraph Container
    AspNetCoreProcess["Server API"]
  end
```
* Angular developer proxy serves the app and runs on the host machine.
* Backend API runs inside the container and receives proxied requests from the app.

The target inside `ClientApp/proxy.conf.js` needs to be updated to target the container URL.
