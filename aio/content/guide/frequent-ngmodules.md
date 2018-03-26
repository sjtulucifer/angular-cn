# Frequently Used Modules

# 常用模块

#### Prerequisites

#### 前提条件

A basic understanding of [Bootstrapping](guide/bootstrapping).

对[引导](guide/bootstrapping)有基本的了解。

<hr>

An Angular app needs at least one module that serves as the root module.
As you add features to your app, you can add them in modules.
The following are frequently used Angular modules with examples
of some of the things they contain:

Angular 应用需要不止一个模块，它们都为根模块服务。
如果你要把某些特性添加到应用中，可以通过添加模块来实现。
下列是一些常用的 Angular 模块，其中带有一些其内容物的例子：

<table>

 <tr>

   <th style="vertical-align: top">

     NgModule

   </th>

   <th style="vertical-align: top">

     Import it from

     导入自

   </th>

   <th style="vertical-align: top">

     Why you use it

     为何使用

   </th>

 </tr>

 <tr>

   <td>

       <code>BrowserModule</code>

   </td>

   <td>

       <code>@angular/platform-browser</code>

   </td>

   <td>

       When you want to run your app in a browser

       当你想要在浏览器中运行应用时

   </td>

 </tr>

 <tr>

   <td>

       <code>CommonModule</code>

   </td>

   <td>

       <code>@angular/common</code>

   </td>

   <td>

       When you want to use <code>NgIf</code>, <code>NgFor</code>

       当你想要使用 <code>NgIf</code> 和 <code>NgFor</code> 时

   </td>

 </tr>

 <tr>

   <td>

       <code>FormsModule</code>

   </td>

   <td>

       <code>@angular/forms</code>

   </td>

   <td>

       When you build template driven forms (includes <code>NgModel</code>)

       当要构建模板驱动表单时（它包含 <code>NgModel</code> ）

   </td>

 </tr>

 <tr>

   <td>

       <code>ReactiveFormsModule</code>

   </td>

   <td>

       <code>@angular/forms</code>

   </td>

   <td>

       When building reactive forms

       当要构建响应式表单时

   </td>

 </tr>

 <tr>

   <td>

       <code>RouterModule</code>

   </td>

   <td>

       <code>@angular/router</code>

   </td>

   <td>

       For Routing and when you want to use <code>RouterLink</code>,<code>.forRoot()</code>, and <code>.forChild()</code>

       要使用路由功能，并且你要用到 <code>RouterLink</code>,<code>.forRoot()</code> 和 <code>.forChild()</code> 时

   </td>

 </tr>

 <tr>

   <td>

       <code>HttpClientModule</code>

   </td>

   <td>

       <code>@angular/common/http</code>

   </td>

   <td>

       When you to talk to a server

       当你要和服务器对话时

   </td>

 </tr>

</table>

## Importing modules

## 导入模块

When you use these Angular modules, import them in `AppModule`,
or your feature module as appropriate, and list them in the `@NgModule`
`imports` array. For example, in the basic app generated by the CLI,
`BrowserModule` is the first import at the top of the `AppModule`,
`app.module.ts`.

当你使用这些 Angular 模块时，在 `AppModule`（或适当的特性模块）中导入它们，并把它们列在当前 `@NgModule` 的 `imports` 数组中。比如，在 CLI 生成的基本应用中，`BrowserModule` 会在 `app.module.ts` 中 `AppModule` 的顶部最先导入。

```typescript

/* import modules so that AppModule can access them */
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [ /* add modules here so Angular knows to use them */
    BrowserModule,
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

The imports at the top of the array are JavaScript import statements
while the `imports` array within `@NgModule` is Angular specific.
For more information on the difference, see [JavaScript Modules vs. NgModules](guide/ngmodule-vs-jsmodule).

文件顶部的这些导入是 JavaScript 的导入语句，而 `@NgModule` 中的 `imports` 数组则是 Angular 特有的。
要了解更多的不同点，参见 [JavaScript 模块 vs. NgModule](guide/ngmodule-vs-jsmodule)。

## `BrowserModule` and `CommonModule`

## `BrowserModule` 和 `CommonModule`

`BrowserModule` imports `CommonModule`, which contributes many common
directives such as `ngIf` and `ngFor`. Additionally, `BrowserModule`
re-exports `CommonModule` making all of its directives available
to any module that imports `BrowserModule`.

`BrowserModule` 导入了 `CommonModule`，它贡献了很多通用的指令，比如 `ngIf` 和 `ngFor`。
另外，`BrowserModule` 重新导出了 `CommonModule`，以便它所有的指令在任何导入了 `BrowserModule` 的 Angular 模块中都可以使用。

For apps that run in the browser, import `BrowserModule` in the
root `AppModule` because it provides services that are essential
to launch and run a browser app. `BrowserModule`’s providers
are for the whole app so it should only be in the root module,
not in feature modules. Feature modules only need the common
directives in `CommonModule`; they don’t need to re-install app-wide providers.

对于运行在浏览器中的应用来说，都必须在根模块中 `AppModule`，因为它提供了启动和运行浏览器应用时某些必须的服务。`BrowserModule` 的提供商是面向整个应用的，所以它只能在根模块中使用，而不是特性模块。
特性模块只需要 `CommonModule` 中的常用指令，它们不需要重新安全所有全应用级的服务。

If you do import `BrowserModule` into a lazy loaded feature module,
Angular returns an error telling you to use `CommonModule` instead.

如果你把 `BrowserModule` 导入了惰性加载的特性模块中，Angular 就会返回一个错误，并告诉你应该改用 `CommonModule`。

<figure>
 <img src="generated/images/guide/frequent-ngmodules/browser-module-error.gif" width=750 alt="BrowserModule error">
</figure>

<hr />

## More on NgModules

## 关于 NgModule 的更多知识

You may also be interested in the following:

你可能还对下列内容感兴趣：

* [Bootstrapping](guide/bootstrapping).

   [引导启动](guide/bootstrapping)。

* [NgModules](guide/ngmodules).

   [Angular 模块](guide/ngmodules).

* [JavaScript Modules vs. NgModules](guide/ngmodule-vs-jsmodule).

   [JavaScript 模块与 NgModules](guide/ngmodule-vs-jsmodule)。