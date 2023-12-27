---
title: Introduction - ElysiaJS
head:
    - - meta
      - property: 'og:title'
        content: Introduction - ElysiaJS

    - - meta
      - name: 'description'
        content: ElysiaJS is a fast and friendly bun web framework. Building on top of 3 philosophies - performance, simplicity, and flexibility. Designed with TypeScript in mind, Elysia understands what you want and automatically infers the type from your code.

    - - meta
      - property: 'og:description'
        content: ElysiaJS is a fast and friendly bun web framework. Building on top of 3 philosophies - performance, simplicity, flexibility. Designed with TypeScript in mind, Elysia understands what you want and automatically infers the type from your code.
---

<script setup>
import Card from '../components/nearl/card.vue'
import Deck from '../components/nearl/card-deck.vue'
</script>

# Introduction

Elysia is an ergonomic web framework for building backend servers for Bun with JavaScript or TypeScript.

Designed with simplicity and type safety in mind, Elysia allows you to create servers with familiar APIs like Express and Fastify.

```typescript
new Elysia()
    .get('/', () => 'hi')
    .get('/id/:id', ({ params: { id } }) => id)
    .post('/form', ({ body }) => body)
    .listen(8080)
```

## Features

What makes Elysia stand out from other frameworks?

-   **Performance** - Static code analysis to generate optimized code
-   **Unified Type** - Shared DTO runtime and compile-time validation
-   **End-to-end Type Safety** - Sync your data across client and server
-   **TypeScript** - Extensive type system for full TypeScript experience
-   **JSX Template Engine** - Familiar experience for frontend developers
-   **Ergonomic by design** - Simple and familiar API for building servers

## Platform Agnostic

Elysia was designed for but **not limited to Bun**. Being [WinterCG compliant](https://wintercg.org/) allows you to deploy the Elysia server on [Cloudflare Workers](https://developers.cloudflare.com/workers/), [Vercel Edge Functions](https://vercel.com/docs/functions/edge-functions), and most other runtimes that support Web Standard Request.

## TypeScript

Elysia is designed to help you write less TypeScript.

Elysia's Type System is fine-tuned to infer types from your code automatically without needing to write explicit TypeScript, while delivering type safety for both runtime and compile-time to provide you with the most ergonomic developer experience.

While it's recommended to use Elysia with TypeScript, you don't need to use TypeScript to use Elysia.

## How to use the documentation

The documentation is **designed to be beginner-friendly**. Basic networking and server concepts will be briefly covered to help beginners understand how the API and behavior of the framework works.

There's **no correct way to learn Elysia**, however we recommended completing the ["Essential" chapter](/essential/route.html) first, as it briefly covers most of Elysia's features and foundation before jumping to other topics that interest you.

As mentioned before, you can use Elysia with other runtimes beside Bun, but the **documentation will assume that you are using Bun**.

On the left side of your screen, you'll find a chapter navigation bar. The pages of the docs are organized sequentially, from basic concepts to more advanced. You can follow them step-by-step to learn about building with Elysia. However, you can read them in any order or skip to the pages that apply to your use case.

On the right side of the screen, you'll find a table of contents for each page for navigation in the page. If you need to find content, **you can use the search bar at the top, or the search shortcut (`Ctrl+K` or `Cmd+K`).**

To get started, check out the [Quick Start guide](https://elysiajs.com/quick-start.html).

## Prerequisite Knowledge

Although Elysia's documentation is designed to be beginner-friendly, we need to establish a baseline so that the docs can stay focused on Elysia's functionality. We will provide links to relevant documentation whenever we introduce a new concept.

To get the most out of our documentation, it's recommended that you have a basic understanding of [Node.js](https://nodejs.org/en) and basic [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP).

## Our Community

If you have questions or get stuck learning about Elysia, feel free to ask our community on [GitHub Discussions](https://github.com/elysiajs), [Discord](https://discord.com/invite/phrduBNq?utm_source=Discord%20Widget&utm_medium=Connect), and [Twitter](https://twitter.com/elysiajs).

<Deck>
    <Card title="Discord" href="https://discord.com/invite/phrduBNq?utm_source=Discord%20Widget&utm_medium=Connect">
        Official ElysiaJS discord community server
    </Card>
    <Card title="Twitter" href="https://twitter.com/elysiajs">
        Track update and status of Elysia
    </Card>
    <Card title="GitHub" href="https://github.com/elysiajs">
        Source code and development
    </Card>
</Deck>
