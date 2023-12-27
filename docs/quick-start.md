---
title: Quick Start - ElysiaJS
head:
    - - meta
      - property: 'og:title'
        content: Quick Start - ElysiaJS

    - - meta
      - name: 'description'
        content: Elysia is a library built for Bun. To start, boostrap a new project with "bun create elysia hi-elysia" and start development server with "bun dev". This is all that's needed to get started with ElysiaJS.

    - - meta
      - property: 'og:description'
        content: Elysia is a library built for Bun. To start, boostrap a new project with "bun create elysia hi-elysia" and start development server with "bun dev". This is all that's needed to get started with ElysiaJS.
---

# Quick Start

System Requirements:

-   [Bun](https://bun.sh)
-   MacOS, Windows (including WSL), and Linux are supported
-   TypeScript > 5.0 (for language server)

## Bun

Elysia is optimized for Bun which is a JavaScript runtime aiming to be an all-in-one runtime & toolkit designed for speed, complete with a bundler, test runner, and Node.js-compatible package manager.

You can install Bun with the command below:

```bash
curl -fsSL https://bun.sh/install | bash
```

## Automatic Installation

We recommend starting a new Elysia server using `bun create elysia`, which sets up everything automatically for you.

To create a project, run:

```bash
bun create elysia app
```

Once done, you should see a folder named `app` in your current directory.

```bash
cd app
```

Start your development server with:

```bash
bun dev
```

Navigating to [localhost:3000](http://localhost:3000) should greet you with "Hello Elysia".

::: tip
Elysia ships with the `dev` command automatically reloading your server on file change.
:::

## Manual Installation

To add manually create an Elysia app, install Elysia as a package:

```typescript
bun add elysia
```

Open your `package.json` file and add the following scripts:

```json
{
    "scripts": {
        "dev": "bun --watch src/index.ts",
        "build": "bun build src/index.ts",
        "start": "NODE_ENV=production bun src/index.ts",
        "test": "bun test"
    }
}
```

These scripts refer to the different stages of developing an application:

-   **dev** - Start Elysia in development mode with auto-reload on code change.
-   **build** - Build the application for production usage.
-   **start** - Start an Elysia production server.

If you are using TypeScript, make sure to create, and update `tsconfig.json` to include `compilerOptions.strict` set to `true`:

```json
{
    "compilerOptions": {
        "strict": true
    }
}
```

## Structure

Here's the recommended file structure for Elysia if you don't strictly prefer a specific convention:

-   **src** - Any file associated with your Elysia server
    -   **index.ts** - Entry point for your Elysia server, ideal place for setting global plugins
    -   **setup.ts** - Composed of various plugins to be used as a [Service Locator](/essential/plugin.html#service-locator)
    -   **controllers** - Instance which encapsulates multiple endpoints
    -   **libs** - Utility functions
    -   **models** - Data Type Objects (DTOs) for Elysia instance
    -   **types** - Shared TypeScript types if needed
-   **test** - Test file for Elysia server
