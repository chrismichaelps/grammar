---
Language: Hono
Version: 4.x
Fidelity: 100% (Physical Disk Reference)
State_ID: BigInt(0x1)
LSP_Discovery_Root: "@root/node_modules/hono/package.json"
Grammar_Lock: "@root/hashes/grammar/hono.hash.md"
---

/** [Project].Grammar.Hono - Linguistic DNA anchor for Hono 4.x */

## [SDK_Discovery_Map]
/** === Core Types (9 definition files) === */
/** @Ref: @root/node_modules/hono/dist/types/index.d.ts */
/** @Ref: @root/node_modules/hono/dist/types/hono.d.ts */
/** @Ref: @root/node_modules/hono/dist/types/hono-base.d.ts */
/** @Ref: @root/node_modules/hono/dist/types/context.d.ts */
/** @Ref: @root/node_modules/hono/dist/types/request.d.ts */
/** @Ref: @root/node_modules/hono/dist/types/compose.d.ts */
/** @Ref: @root/node_modules/hono/dist/types/http-exception.d.ts */
/** @Ref: @root/node_modules/hono/dist/types/router.d.ts */
/** @Ref: @root/node_modules/hono/dist/types/types.d.ts */

## [SDK_Imports / Namespaces]
```ts
import { Hono } from "hono"
import type { Context, Next, MiddlewareHandler, Handler, Env, Schema, TypedResponse, HonoRequest } from "hono"
import { HTTPException } from "hono/http-exception"

// Middleware
import { cors } from "hono/cors"
import { logger } from "hono/logger"
import { prettyJSON } from "hono/pretty-json"
import { secureHeaders } from "hono/secure-headers"
import { basicAuth } from "hono/basic-auth"
import { bearerAuth } from "hono/bearer-auth"
import { jwt, sign, verify } from "hono/jwt"
import { compress } from "hono/compress"
import { cache } from "hono/cache"
import { etag } from "hono/etag"
import { timing } from "hono/timing"
import { bodyLimit } from "hono/body-limit"

// Validators
import { validator } from "hono/validator"
import { zValidator } from "@hono/zod-validator"

// RPC client
import { hc } from "hono/client"
import type { InferRequestType, InferResponseType } from "hono/client"

// Helpers
import { html, raw } from "hono/html"
import { stream, streamSSE, streamText } from "hono/streaming"
import { createFactory, createMiddleware } from "hono/factory"
import { setCookie, getCookie, deleteCookie } from "hono/cookie"

// Adapters
import { serve } from "@hono/node-server"
import { handle } from "hono/vercel"
import { handle } from "hono/aws-lambda"
```

## [Core_Primitives]
```ts
// App creation (hono.d.ts, hono-base.d.ts)
const app = new Hono<{ Bindings: Env; Variables: Vars }>()

// Env type (generic type parameter)
type Env = {
  Bindings: { DATABASE_URL: string; API_KEY: string }  // platform bindings (CF Workers, etc.)
  Variables: { user: User; requestId: string }           // per-request variables via c.set/c.get
}

// Context (context.d.ts — the heart of Hono)
interface Context<E extends Env = any, P extends string = any, I extends Input = {}> {
  // Request
  req: HonoRequest<P, I["out"]>
  
  // Response builders
  json<T>(data: T, status?: StatusCode, headers?: HeaderRecord): TypedResponse<T>
  text(text: string, status?: StatusCode, headers?: HeaderRecord): Response
  html(html: string | Promise<string>, status?: StatusCode, headers?: HeaderRecord): Response
  body(data: string | ArrayBuffer | ReadableStream | null, status?: StatusCode, headers?: HeaderRecord): Response
  redirect(location: string, status?: RedirectStatusCode): Response
  notFound(): Response | Promise<Response>
  
  // Headers
  header(name: string, value: string, options?: { append?: boolean }): void
  
  // Variables (type-safe per-request storage)
  set<Key extends keyof E["Variables"]>(key: Key, value: E["Variables"][Key]): void
  get<Key extends keyof E["Variables"]>(key: Key): E["Variables"][Key]
  var: E["Variables"]  // shorthand access
  
  // Platform bindings
  env: E["Bindings"]
  
  // Execution context (Cloudflare Workers)
  executionCtx: ExecutionContext
  event: FetchEvent
  
  // Error
  error?: Error
  
  // Finalized response
  finalized: boolean
  res: Response
}

// HonoRequest (request.d.ts)
interface HonoRequest<P extends string = "/", I = {}> {
  url: string
  method: string
  path: string
  raw: Request  // Web Standard Request
  
  param<Key extends keyof ParamKeys<P>>(key: Key): string
  param(): Record<string, string>
  query(key: string): string | undefined
  query(): Record<string, string>
  queries(key: string): string[] | undefined
  queries(): Record<string, string[]>
  header(name: string): string | undefined
  header(): Record<string, string>
  
  parseBody(options?: ParseBodyOptions): Promise<Record<string, string | File>>
  json<T>(): Promise<T>
  text(): Promise<string>
  arrayBuffer(): Promise<ArrayBuffer>
  blob(): Promise<Blob>
  formData(): Promise<FormData>
  
  valid<Type extends keyof I>(type: Type): I[Type]  // validated data access
  
  matchedRoutes: RouterRoute[]
  routePath: string
}

// HTTPException (http-exception.d.ts)
class HTTPException extends Error {
  status: StatusCode
  res?: Response
  getResponse(): Response
  constructor(status?: StatusCode, options?: { message?: string; res?: Response; cause?: unknown })
}
```

## [Architectural_Laws]
- **Export_Law**: Export app instance and typed routes for RPC client. Use `export type AppType = typeof app` for hc() client inference. Export middleware via factory functions.
- **Transformation_Law**: Web Standard API based — Request/Response everywhere. Works on every runtime: Cloudflare Workers, Deno, Bun, Node.js, AWS Lambda, Vercel Edge. Middleware composition via `app.use()`. Type-safe RPC via `hc<AppType>()`.
- **Propagation_Law**: Throw `HTTPException` for HTTP errors. Use `.onError()` for global error handling. Use `.notFound()` for 404 handler. Errors in middleware propagate to error handler.

## [Syntax_Rules] | [Naming_Conventions]
- camelCase: routes, middleware, handlers
- kebab-case: URL paths
- PascalCase: types, Hono app
- `:param`: path parameter syntax
- `*`: wildcard syntax

## [Prohibited_Patterns]
- NO Node.js-specific APIs in edge-targeted code — Hono is Web Standard
- NO `c.json()` without `return` — response must be returned
- NO mutation of `c.res` after `c.json()`/`c.text()` — already finalized
- NO untyped `c.req.body` — use `c.req.json<T>()` or validators

## [Standard_Library_Signatures]
```ts
// Route registration
app.get(path: string, ...handlers: Handler[]): Hono
app.post(path: string, ...handlers: Handler[]): Hono
app.put(path: string, ...handlers: Handler[]): Hono
app.delete(path: string, ...handlers: Handler[]): Hono
app.patch(path: string, ...handlers: Handler[]): Hono
app.options(path: string, ...handlers: Handler[]): Hono
app.all(path: string, ...handlers: Handler[]): Hono
app.on(method: string | string[], path: string | string[], ...handlers: Handler[]): Hono

// Middleware
app.use(path?: string, ...middleware: MiddlewareHandler[]): Hono

// Grouping / Mounting
app.route(path: string, subApp: Hono): Hono
app.basePath(path: string): Hono

// Error handling
app.onError((err: Error, c: Context) => Response | Promise<Response>): Hono
app.notFound((c: Context) => Response | Promise<Response>): Hono

// Zod validation (via @hono/zod-validator)
app.post("/", zValidator("json", z.object({ name: z.string() })), (c) => {
  const { name } = c.req.valid("json")  // fully typed
  return c.json({ name })
})

// RPC client (hono/client)
const client = hc<AppType>("http://localhost:8787")
const res = await client.api.users.$get()          // typed request
const data = await res.json()                       // typed response
type ReqType = InferRequestType<typeof client.api.users.$post>
type ResType = InferResponseType<typeof client.api.users.$post>

// Streaming (hono/streaming)
app.get("/stream", (c) => stream(c, async (stream) => {
  await stream.write("chunk 1")
  await stream.write("chunk 2")
}))
app.get("/sse", (c) => streamSSE(c, async (stream) => {
  await stream.writeSSE({ data: JSON.stringify({ msg: "hello" }), event: "update", id: "1" })
}))

// Cookies (hono/cookie)
setCookie(c, "name", "value", { path: "/", httpOnly: true, maxAge: 3600 })
getCookie(c, "name"): string | undefined
deleteCookie(c, "name")

// Fetch handler (for platforms)
export default app                         // Cloudflare Workers / Bun
export default { port: 3000, fetch: app.fetch } // Bun
```
