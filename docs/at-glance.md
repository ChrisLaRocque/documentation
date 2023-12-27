---
title: At a glance - ElysiaJS
head:
    - - meta
      - property: 'og:title'
        content: At a glance - ElysiaJS

    - - meta
      - name: 'description'
        content: Elysia is designed with familiar APIs from Express and Fastify, with extensive support for TypeScript, a modern JavaScript API and optimized for Bun.

    - - meta
      - property: 'og:description'
        content: Elysia is designed with familiar APIs from Express and Fastify, with extensive support for TypeScript, a modern JavaScript API and optimized for Bun.
---

# At a glance

Elysia is designed with familiar APIs from Express and Fastify, with extensive support for TypeScript, a modern JavaScript API and optimized for Bun.

Here's a simple hello world in Elysia.

```typescript
import { Elysia } from 'elysia'

new Elysia().get('/', () => 'Hello Elysia').listen(3000)
```

Navigating to [localhost:3000](http://localhost:3000/) should show 'Hello Elysia' as a result.

## Performance

Elysia builds on Bun's extensive optimizations while adding its own, like Static Code Analysis which allows Elysia to generate optimized code on the fly.

Elysia can out-perform most of the web frameworks available today<a href="#ref-1"><sup>[1]</sup></a>, and even match the performance of Go and Rust <a href="#ref-2"><sup>[2]</sup></a>.

| Framework     | Runtime | Average     | Plain Text | Dynamic Parameters | JSON Body  |
| ------------- | ------- | ----------- | ---------- | ------------------ | ---------- |
| Elysia        | bun     | 275,063.507 | 326,868.9  | 261,729.3          | 236,592.32 |
| Bun           | bun     | 273,634.127 | 322,071.07 | 251,679.46         | 247,151.85 |
| Hono          | bun     | 257,532.08  | 320,757.07 | 233,769.22         | 218,069.95 |
| Web Standard  | bun     | 242,838.703 | 288,692.76 | 226,591.45         | 213,231.9  |
| Hyper Express | node    | 242,045.913 | 354,697.63 | 277,109.51         | 94,330.6   |
| h3            | node    | 112,677.263 | 137,556.49 | 101,431.5          | 99,043.8   |
| Fastify       | node    | 64,145.95   | 74,631.46  | 66,235.48          | 51,570.91  |
| Koa           | node    | 38,696.13   | 44,741.88  | 39,790.11          | 31,556.4   |
| Hapi          | node    | 28,170.763  | 42,780.44  | 15,350.06          | 26,381.79  |
| Adonis        | node    | 23,367.073  | 22,673.54  | 21,442.97          | 25,984.71  |
| Express       | node    | 16,301.823  | 17,974.35  | 17,090.62          | 13,840.5   |
| Nest          | node    | 14,978.863  | 16,926.01  | 15,507.62          | 12,502.96  |

## TypeScript

Elysia is built with a complex type system which attempts to infer every possible detail from thigns as simple as path parameters, to full-blown recursive instance deep merge to provide you the most out of TypeScript.

Take a look at this example:

```typescript
import { Elysia } from 'elysia'

new Elysia().get('/id/:id', ({ params: { id } }) => id).listen(8080)
```

The above code allows you to create a path parameter with the name of id, the value passed in the URL after `/id/` will be reflected as `params.id`.

In most framework, you need to provide a generic type to the **id** parameter while Elysia understand that `params.id` will always be available and typed as **string**. Elysia then infers this type without any manual type references need.

Elysia's goal is to help you write less TypeScript and focus more on business logic. Let the complex types be handled by the framework.

## Unified Type

To take types a step further, Elysia provides **Elysia.t**, a schema builder to validate types and their values in both runtime and compile-time to create a single source of truth for your data types. Elysia refers to this as a **Unified Type**.

Let's modify the previous code to accept only a numeric value instead of string.

```typescript
import { Elysia, t } from 'elysia'

new Elysia()
    .get('/id/:id', ({ params: { id } }) => id, {
        params: t.Object({
            id: t.Numeric()
        })
    })
    .listen(8080)
```

This code ensures that our path parameter **id**, will always be a numeric string and then transform it to a number automatically in both runtime, and compile-time (type-level).

With Elysia's `t` schema builder, we can ensure type safety like a strong typed language with a single source of truth.

## Standard

Elysia adopts many standards by default, like [OpenAPI](https://www.openapis.org/), and [WinterCG](https://wintercg.org/) compilance, allowing you to integrate with most industry standard tools or at least easily integrate with tools you are familiar with.

For instance, as Elysia adopted OpenAPI by default, generating documentation with [Swagger](https://swagger.io/) is as easy as adding one line:

```typescript
import { Elysia, t } from 'elysia'
import { swagger } from '@elysiajs/swagger'

new Elysia()
    .use(swagger())
    .get('/id/:id', ({ params: { id } }) => id, {
        params: t.Object({
            id: t.Numeric()
        })
    })
    .listen(8080)
```

With the [Swagger plugin](/plugins/swagger.html#swagger-plugin), you can seamlessly generate a Swagger documentation page without additional code or specific config and share with your team effortlessly.

## End-to-end Type Safety

With Elysia, type safety is not limited to server-side only.

With Elysia, you can synchronize your types with your frontend team automacially like tRPC, with [Elysia's client library, "Eden"](https://github.com/elysiajs/eden).

```typescript
import { Elysia, t } from 'elysia'
import { swagger } from '@elysiajs/swagger'

new Elysia()
    .use(swagger())
    .get('/id/:id', ({ params: { id } }) => id, {
        params: t.Object({
            id: t.Numeric()
        })
    })
    .listen(8080)

export type App = typeof app
```

And on your client-side:

```typescript
// client.ts
import { edenTreaty } from '@elysiajs/eden'
import type { App } from './server'

const app = edenTreaty<App>('http://localhost:8080')

// data is typed as number
const { data } = await app.id['177013'].get()
```

With Eden, you can use existing Elysia types to query the Elysia server **without code generation** and synchronize types for both frontend and backend automatically.

Elysia is not only about helping you to create a reliable backend, but for all that is beautiful in this world.

---

<small id="ref-1">1. Measure in requests/second. Benchmark for parsing query, path parameter and set response header on Debian 11, Intel i7-13700K tested on Bun 0.7.2 at 6 Aug 2023. See the benchmark condition [here](https://github.com/SaltyAom/bun-http-framework-benchmark/tree/c7e26fe3f1bfee7ffbd721dbade10ad72a0a14ab#results).</small>

<small id="ref-2">2. Based on [TechEmpower Benchmark round 22](https://www.techempower.com/benchmarks/#section=data-r22&hw=ph&test=composite).</small>
