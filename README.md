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
  SpinalForgeExtention
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

## Functions

<dl>
<dt><a href="#createExtention">createExtention(option)</a> ⇒</dt>
<dd><p>factory function to create a dynamic class that extends the <code>SpinalPanelApp</code> class</p>
<pre><code class="language-javascript">{
  name: &quot;extention_name&quot;,
  vueMountComponent: Vue.extend(aVueCompoment),
  onLoad: () =&gt; {console.log(&quot;onLoad&quot;);},
  onUnLoad: () =&gt; {console.log(&quot;onUnLoad&quot;);},
  toolbar: {
    icon: &quot;done&quot;,
    label: &quot;testLabel&quot;,
    subToolbarName: &quot;spinalcom&quot;
  },
  panel: {
    title: &quot;Spinalcom Panel&quot;,
    classname: &quot;spinal-pannel&quot;,
    closeBehaviour: &quot;hide&quot;
  },
  style: {}
}
</code></pre>
</dd>
<dt><a href="#registerExtention">registerExtention(name, classExtention)</a></dt>
<dd><p>Method to register an extention to the viewer and the forge viewer</p>
</dd>
</dl>

<a name="createExtention"></a>

## createExtention(option) ⇒
factory function to create a dynamic class that extends the `SpinalPanelApp` class
```js
{
  name: "extention_name",
  vueMountComponent: Vue.extend(aVueCompoment),
  onLoad: () => {console.log("onLoad");},
  onUnLoad: () => {console.log("onUnLoad");},
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
  style: {}
}
```

**Kind**: global function  
**Returns**: SpinalForgeExtention  

| Param | Type | Description |
| --- | --- | --- |
| option | <code>object</code> | see description |


* [createExtention(option)](#createExtention) ⇒
    * [~SpinalForgeExtention](#createExtention..SpinalForgeExtention) ⇐ <code>SpinalPanelApp</code>
        * [.load()](#createExtention..SpinalForgeExtention+load)
        * [.unload()](#createExtention..SpinalForgeExtention+unload)
        * [.openPanel(option)](#createExtention..SpinalForgeExtention+openPanel)
        * [.closePanel(option)](#createExtention..SpinalForgeExtention+closePanel)
        * [.tooglePanel(option)](#createExtention..SpinalForgeExtention+tooglePanel)

<a name="createExtention..SpinalForgeExtention"></a>

### createExtention~SpinalForgeExtention ⇐ <code>SpinalPanelApp</code>
class returned by createExtention
this extention is also registered in autodesk viweer

**Kind**: inner class of [<code>createExtention</code>](#createExtention)  
**Extends**: <code>SpinalPanelApp</code>  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| viewer | <code>AutodeskViewer</code> | the autodesk view |
| panel | <code>AutodeskPanel</code> | the panel |
| compoment | <code>Vue.component</code> | the compoment mounted |
| cfg | <code>Object</code> | the option given on creation |


* [~SpinalForgeExtention](#createExtention..SpinalForgeExtention) ⇐ <code>SpinalPanelApp</code>
    * [.load()](#createExtention..SpinalForgeExtention+load)
    * [.unload()](#createExtention..SpinalForgeExtention+unload)
    * [.openPanel(option)](#createExtention..SpinalForgeExtention+openPanel)
    * [.closePanel(option)](#createExtention..SpinalForgeExtention+closePanel)
    * [.tooglePanel(option)](#createExtention..SpinalForgeExtention+tooglePanel)

<a name="createExtention..SpinalForgeExtention+load"></a>

#### spinalForgeExtention.load()
method called on load of the extention (managed by the autodesk viewer)
the method create a button in the toolbar if put in the option of `createExtention`.

**Kind**: instance method of [<code>SpinalForgeExtention</code>](#createExtention..SpinalForgeExtention)  
<a name="createExtention..SpinalForgeExtention+unload"></a>

#### spinalForgeExtention.unload()
method called when the viewer unload of the extention
(managed by the autodesk viewer)

**Kind**: instance method of [<code>SpinalForgeExtention</code>](#createExtention..SpinalForgeExtention)  
<a name="createExtention..SpinalForgeExtention+openPanel"></a>

#### spinalForgeExtention.openPanel(option)
**Kind**: instance method of [<code>SpinalForgeExtention</code>](#createExtention..SpinalForgeExtention)  

| Param | Type |
| --- | --- |
| option | <code>\*</code> | 

<a name="createExtention..SpinalForgeExtention+closePanel"></a>

#### spinalForgeExtention.closePanel(option)
**Kind**: instance method of [<code>SpinalForgeExtention</code>](#createExtention..SpinalForgeExtention)  

| Param | Type |
| --- | --- |
| option | <code>\*</code> | 

<a name="createExtention..SpinalForgeExtention+tooglePanel"></a>

#### spinalForgeExtention.tooglePanel(option)
**Kind**: instance method of [<code>SpinalForgeExtention</code>](#createExtention..SpinalForgeExtention)  

| Param | Type |
| --- | --- |
| option | <code>\*</code> | 

<a name="registerExtention"></a>

## registerExtention(name, classExtention)
Method to register an extention to the viewer and the forge viewer

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | name of the extention |
| classExtention | <code>\*</code> | an extention created by `createExtention` |


---
