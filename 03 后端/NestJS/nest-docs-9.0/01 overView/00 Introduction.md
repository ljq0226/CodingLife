# Introduction
Nest (NestJS) is a framework for building **efficient, scalable** Node.js **server-side** applications. It uses **progressive** JavaScript, is built with and fully *supports TypeScript* (yet still enables developers to code in pure JavaScript) and combines elements of **OOP** (Object Oriented Programming), **FP** (Functional Programming), and **FRP** (Functional Reactive Programming).

Under the hood, Nest **makes use of robust HTTP Server frameworks** like **Express** (the default) and optionally can be configured to use **Fastify** as well!

Nest provides **a level of abstraction** above these common Node.js frameworks (Express/Fastify), but also **exposes their APIs** directly to the developer. This gives developers the freedom to use the myriad of third-party modules which are available for the underlying platform.
```ad-note
NestJS是一个完全支持TypeScript的高效、可拓展的nodejs服务端开发框架，基于Express\Fastify提供HTTP Server优秀框架并同时暴露出其所有API以供使用。
```
# Philosophy
In recent years, thanks to Node.js, JavaScript has become the “lingua franca”(通用语) of the web for both front and backend applications. This has given rise to awesome projects like Angular, React and Vue, which improve developer productivity and enable the creation of **fast**, **testable**, and **extensible** **frontend applications**. However, while plenty of superb libraries, helpers, and tools exist for Node (and server-side JavaScript), **none of them effectively solve the main problem of - Architecture**（架构）.

Nest provides an *out-of-the-box application architecture* which allows developers and teams to create highly **testable, scalable, loosely coupled（低耦合）, and easily maintainable** applications. The architecture is heavily inspired by Angular.
```ad-note
基于 JavaScript 在前端圈的影响，Nest 提供了一个允许 developers 和 teams 创建高度可测试、可伸缩、低耦合、易于维护的应用开箱即用的应用架构。
```
# Installation
To get started, you can either scaffold the project with the Nest CLI, or clone a starter project (both will produce the same outcome).

To **scaffold**(搭建脚手架) the project with the Nest CLI, run the following commands. This will create a new project directory, and **populate** the directory with the initial core Nest files and supporting modules, creating a conventional base structure for your project. Creating a new project with the Nest CLI is recommended for first-time users. We'll continue with this approach in First Steps.

```code
$ npm i -g @nestjs/cli
$ nest new project-name
```

```ad-hint
若要开启 strict 模式,在上面的命令后加上 --strict
```


