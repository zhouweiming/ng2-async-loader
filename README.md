# ng2-async-loader

配合angular2-rc5的lazy loading在webpack中的发布。

##说明

1. 适用于使用了angular-rc5的lazy loading进行路由管理，并结合webpack进行发布的工程。


##使用

```
routes:

import { asyncWrap } from "async-loader";

let routes: Routes = [
  {
    path: "demo",
    loadChildren: asyncWrap(() => {
      return require("../demo/demo.module");
    })
  }
]

```

```
AppModule:

import { NgModule, NgModuleFactoryLoader } from "@angular/core";
import { AsyncNgModuleLoader } from "async-loader";

@NgModule({
  providers: [
    { provide: NgModuleFactoryLoader, useClass: AsyncNgModuleLoader }
  ]
})
export class AppModule{}
```