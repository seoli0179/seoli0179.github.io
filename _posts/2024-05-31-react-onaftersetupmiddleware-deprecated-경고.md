---
layout: post
title: "[React] onAfterSetupMiddleware Deprecated 경고"
category:
- CS
- React
tags:
- React
- Debug
date: 2024-05-31 20:51 +0900
---
# onAfterSetupMiddleware, onBeforeSetupMiddleware Deprecated 경고 메시지 발생

```console
(node:25372) [DEP_WEBPACK_DEV_SERVER_ON_AFTER_SETUP_MIDDLEWARE] DeprecationWarning: 'onAfterSetupMiddleware' option is deprecated. Please use the 'setupMiddlewares' option.
(Use `node --trace-deprecation ...` to show where the warning was created)
(node:25372) [DEP_WEBPACK_DEV_SERVER_ON_BEFORE_SETUP_MIDDLEWARE] DeprecationWarning: 'onBeforeSetupMiddleware' option is deprecated. Please use the 'setupMiddlewares' option.
```

## 변경 전
```
onBeforeSetupMiddleware(devServer) {
      // Keep `evalSourceMapMiddleware`
      // middlewares before `redirectServedPath` otherwise will not have any effect
      // This lets us fetch source contents from webpack for the error overlay
      devServer.app.use(evalSourceMapMiddleware(devServer));

      if (fs.existsSync(paths.proxySetup)) {
        // This registers user provided middleware for proxy reasons
        require(paths.proxySetup)(devServer.app);
      }
    },
    onAfterSetupMiddleware(devServer) {
      // Redirect to `PUBLIC_URL` or `homepage` from `package.json` if url not match
      devServer.app.use(redirectServedPath(paths.publicUrlOrPath));

      // This service worker file is effectively a 'no-op' that will reset any
      // previous service worker registered for the same host:port combination.
      // We do this in development to avoid hitting the production cache if
      // it used the same host and port.
      // https://github.com/facebook/create-react-app/issues/2272#issuecomment-302832432
      devServer.app.use(noopServiceWorkerMiddleware(paths.publicUrlOrPath));
    },
```
{: file='node_modules\react-scripts\config\webpackDevServer.config.js'}

## 변경 후
```
setupMiddlewares: (middlewares, devServer) => {
      if(!devServer) {
        throw new Error('webpack-dev-server is not defined')
      }

      if(fs.existsSync(paths.proxySetup)) {
        require(paths.proxySetup)(devServer.app)
      }

      middlewares.push(
          evalSourceMapMiddleware(devServer),
          redirectServedPath(paths.publicUrlOrPath),
          noopServiceWorkerMiddleware(paths.publicUrlOrPath)
      )

      return middlewares;
    },
```
{: file='node_modules\react-scripts\config\webpackDevServer.config.js'}
