#### Language

We're in love with [TypeScript](https://www.typescriptlang.org/), but above all - we love [Node.js](https://nodejs.org/en/). That's why Nest is compatible with both TypeScript and **pure JavaScript**. Nest takes advantage of the latest language features, so to use it with vanilla JavaScript we need a [Babel](https://babeljs.io/) compiler.

We'll mostly use TypeScript in the examples we provide, but you can always **switch the code snippets** to vanilla JavaScript syntax (simply click to toggle the language button in the upper right hand corner of each snippet).

#### Prerequisites

Please make sure that [Node.js](https://nodejs.org) (version >= 12, except for v13) is installed on your operating system.

#### Setup
After created by nest scaffold,the Project Structure be like this.
![](https://obs-pic-1309372570.cos.ap-chongqing.myqcloud.com/20221003211142.png)
Here's a brief overview of those core files:

| app.controller.ts      | A basic controller with a single route |
| ---------------------- | -------------------------------------- |
| app.controller.spec.ts | The unit tests for the controller.     |
| app.module.ts                       |     The root module of the application.                                  |
|  app.service.ts                      |  A basic service with a single method.                                      |
| main.ts                      |   The entry file of the application which uses the core function `NestFactory` to create a Nest application instance.                                     |

The `main.ts` includes an async function, which will **bootstrap** our application:
```typescript
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}
bootstrap();
```

To create a Nest application instance, we use the core `NestFactory` class. `NestFactory` exposes a few static methods that allow creating an application instance. The `create()` method **returns an application object**, which **fulfills** the `INestApplication` interface. This object provides a set of methods which are described in the coming chapters. In the `main.ts` example above, we simply start up our HTTP listener, which lets the application await inbound HTTP requests.

Note that a project scaffolded with the Nest CLI creates an initial project structure that encourages developers to follow the convention of keeping each module in its own dedicated directory.
```ad-note
通过 '@nestjs/core' 提供的一个 NestFactory 创建实例，该实例app实现了 INestApplication 接口，包含很多 Nest 方法函数（拦截器、管道等）
```

```ad-hint
By default, if any error happens while creating the application your app will exit with the code `1`. If you want to make it throw an error instead disable the option `abortOnError` (e.g., `NestFactory.create(AppModule, { abortOnError: false })`).
```

#### Platform
Nest aims to be a **platform-agnostic**(平台无关) framework. Platform independence makes it possible to create reusable logical parts that developers can take advantage of across several different types of applications. Technically, Nest is able to work with any Node HTTP framework once an adapter is created. There are two HTTP platforms supported out-of-the-box: express and fastify. **You can choose the one that best suits your needs**.

| platform-express | Express is a well-known minimalist web framework for node. It's a battle tested, production-ready library with lots of resources implemented by the community. The @nestjs/platform-express package is used by default. Many users are well served with Express, and need take no action to enable it. |
| ---------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| platform-fastify | Fastify is a high performance and low overhead framework highly focused on providing maximum efficiency and speed. Read how to use it here.                                                                                                                                                            |

Whichever platform is used, it exposes its own application interface. These are seen respectively as NestExpressApplication and NestFastifyApplication.                                                                                                                                                                                                                                                                                          

When you pass a type to the NestFactory.create() method, as in the example below, the app object will have methods available exclusively for that specific platform. Note, however, you don't need to specify a type unless you actually want to access the underlying platform API.
```ad-note
Nest提供了两种提供 HTTP 服务的底层平台，只需要在 create 函数后添加上提供的的类型即可。 
```

```ts

import { NestExpressApplication } from '@nestjs/platform-express';
···
  const app = await NestFactory.create<NestExpressApplication>(AppModule);
···
```

#### Running the application

Once the installation process is complete, you can run the following command at your OS command prompt to start the application listening for inbound HTTP requests:

```bash
$ npm run start
```

This command starts the app with the HTTP server listening on the port defined in the `src/main.ts` file. Once the application is running, open your browser and navigate to `http://localhost:3000/`. You should see the `Hello World!` message.

To watch for changes in your files, you can run the following command to start the application:

```bash
$ npm run start:dev
```

This command will watch your files, automatically recompiling and reloading the server.