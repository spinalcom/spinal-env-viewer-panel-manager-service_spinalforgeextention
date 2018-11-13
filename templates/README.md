# spinal-env-viewer-panel-manager-service_spinalforgeextention

spinal-env-viewer-panel-manager-service_spinalforgeextention is an extention of spinal-env-viewer-panel-manager-service to warp the creation of panel in the forge viewer

## Installation

```sh
npm i --save https://github.com/spinalcom/spinal-env-viewer-panel-manager-service_spinalforgeextention
```

## Usage

Get the service instances and factory.

```js
const {
  SpinalMountExtention
} = require("spinal-env-viewer-panel-manager-service_spinalforgeextention");
```

```js
import Vue from "vue";
import aVueCompoment from "./testCompoment.vue";

const extentionCreated = SpinalForgeExtention.createExtention({
  name: "my_test_Extention",
  vueMountComponent: Vue.extend(aVueCompoment),
  toolbar: {
    icon: "done",
    label: "testLabel",
    subToolbarName: "spinalcom"
  },
  panel: {
    title: "Spinalcom Panel",
    classname: "spinal-pannel",
    closeBehaviour: "hide"
  },
  style: {
    left: "405px"
  }
});

SpinalForgeExtention.registerExtention("my_test_Extention", extentionCreated);
```

### Build transform config

Add some build config for browserify in the `package.json`.

```json
...
  "browserify": {
    "transform": [
      "vueify",
      "babelify"
    ]
  }
...
```

## Open the compoment

Later we can open the mounted compoment via an button (or something else) via the `openPanel` method.

```js
const {
  spinalPanelManagerService
} = require("spinal-env-viewer-panel-manager-service_spinalforgeextention");

spinalPanelManagerService.openPanel("myCustomDialogName", {
  initialValue: "hello"
});
```

---

## API Documentations

{{>main}}

---
