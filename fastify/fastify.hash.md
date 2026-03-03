---
Language: Fastify
Version: 5.x
Fidelity: 100% (Physical Disk Reference)
State_ID: BigInt(0x1)
LSP_Discovery_Root: "@root/node_modules/fastify/package.json"
Grammar_Lock: "@root/hashes/grammar/fastify.hash.md"
---

/** [Project].Grammar.Fastify - Linguistic DNA anchor for Fastify 5.x */

## [SDK_Discovery_Map]
/** === Core (16 definition files) === */
/** @Ref: @root/node_modules/fastify/fastify.d.ts */
/** @Ref: @root/node_modules/fastify/types/instance.d.ts */
/** @Ref: @root/node_modules/fastify/types/request.d.ts */
/** @Ref: @root/node_modules/fastify/types/reply.d.ts */
/** @Ref: @root/node_modules/fastify/types/route.d.ts */
/** @Ref: @root/node_modules/fastify/types/hooks.d.ts */
/** @Ref: @root/node_modules/fastify/types/plugin.d.ts */
/** @Ref: @root/node_modules/fastify/types/register.d.ts */
/** @Ref: @root/node_modules/fastify/types/schema.d.ts */
/** @Ref: @root/node_modules/fastify/types/type-provider.d.ts */
/** @Ref: @root/node_modules/fastify/types/content-type-parser.d.ts */
/** @Ref: @root/node_modules/fastify/types/errors.d.ts */
/** @Ref: @root/node_modules/fastify/types/logger.d.ts */
/** @Ref: @root/node_modules/fastify/types/context.d.ts */
/** @Ref: @root/node_modules/fastify/types/server-factory.d.ts */
/** @Ref: @root/node_modules/fastify/types/utils.d.ts */

## [SDK_Imports / Namespaces]
```ts
import Fastify from "fastify"
import type { FastifyInstance, FastifyRequest, FastifyReply, FastifySchema, FastifyPluginAsync, FastifyPluginCallback, FastifyPluginOptions, FastifyError, FastifyListenOptions, FastifyRegisterOptions, FastifyTypeProvider, FastifyTypeProviderDefault, FastifyBaseLogger, RouteShorthandOptions, RouteHandlerMethod, RouteGenericInterface, FastifyServerOptions, FastifyHttp2Options, FastifyHttp2SecureOptions, FastifyLoggerOptions, RegisterOptions, RawServerDefault, RawRequestDefaultExpression, RawReplyDefaultExpression, preHandlerHookHandler, preValidationHookHandler, preSendHookHandler, onRequestHookHandler, onResponseHookHandler, onErrorHookHandler, preParsingHookHandler, onTimeoutHookHandler, preSerializationHookHandler, onSendHookHandler, onReadyHookHandler, onListenHookHandler, onCloseHookHandler } from "fastify"
```

## [Core_Primitives]
```ts
// Server creation (fastify.d.ts)
const app = Fastify({
  logger?: boolean | FastifyLoggerOptions,
  disableRequestLogging?: boolean,
  caseSensitive?: boolean,
  ignoreTrailingSlash?: boolean,
  ignoreDuplicateSlashes?: boolean,
  maxParamLength?: number,
  bodyLimit?: number,
  connectionTimeout?: number,
  keepAliveTimeout?: number,
  pluginTimeout?: number,
  requestIdHeader?: string | false,
  requestIdLogLabel?: string,
  genReqId?: (req) => string,
  trustProxy?: boolean | string | string[] | number,
  ajv?: { customOptions?, plugins? },
  serializerOpts?: { schema?, ajv?, rpiOpts? },
  http2?: boolean,
  https?: { key, cert, ... },
  serverFactory?: ServerFactory,
  return503OnClosing?: boolean,
  forceCloseConnections?: boolean | "idle",
})

// FastifyRequest<RouteGeneric> (types/request.d.ts)
interface FastifyRequest<RouteGeneric extends RouteGenericInterface = RouteGenericInterface> {
  id: string
  params: RouteGeneric["Params"]
  raw: RawRequestDefaultExpression
  query: RouteGeneric["Querystring"]
  body: RouteGeneric["Body"]
  headers: RouteGeneric["Headers"]
  log: FastifyBaseLogger
  server: FastifyInstance
  url: string
  method: string
  routerPath: string
  routerMethod: string
  routeOptions: { url: string; method: string; bodyLimit: number; logLevel: string }
  ip: string
  ips?: string[]
  hostname: string
  protocol: "http" | "https"
  is404: boolean
  socket: Socket
  context: FastifyContext
  getValidationFunction(schema: { httpPart: string }): ValidateFunction
  compileValidationSchema(schema: object, httpPart?: string): ValidateFunction
  validateInput(input: unknown, schema: object | string, httpPart?: string): boolean
}

// FastifyReply (types/reply.d.ts)
interface FastifyReply {
  raw: RawReplyDefaultExpression
  code(statusCode: number): this
  status(statusCode: number): this
  statusCode: number
  header(key: string, value: string): this
  headers(values: Record<string, string>): this
  getHeader(key: string): string | undefined
  getHeaders(): Record<string, string | string[]>
  removeHeader(key: string): this
  hasHeader(key: string): boolean
  type(contentType: string): this
  redirect(url: string, code?: number): this
  callNotFound(): void
  serialize(payload: unknown): string
  serializer(fn: (payload: unknown) => string): this
  send(payload?: unknown): this
  then(onfulfilled, onrejected): Promise<void>
  elapsedTime: number
  log: FastifyBaseLogger
  request: FastifyRequest
  server: FastifyInstance
}

// RouteGenericInterface (types/route.d.ts)
interface RouteGenericInterface {
  Body?: unknown
  Querystring?: unknown
  Params?: unknown
  Headers?: unknown
  Reply?: unknown
}

// Type Provider (types/type-provider.d.ts) — Zod/TypeBox integration
interface FastifyTypeProvider { readonly input: unknown; readonly output: unknown }
interface FastifyTypeProviderDefault extends FastifyTypeProvider { readonly output: this["input"] }
```

## [Hooks_Lifecycle]
```ts
// Request lifecycle hooks (types/hooks.d.ts) — IN ORDER
onRequest     → preParsing  → preValidation → preHandler →
// route handler executes here
preSerialization → onSend   → onResponse

// Hook signatures
app.addHook("onRequest", async (request, reply) => {})
app.addHook("preParsing", async (request, reply, payload) => { return modifiedPayload })
app.addHook("preValidation", async (request, reply) => {})
app.addHook("preHandler", async (request, reply) => {})
app.addHook("preSerialization", async (request, reply, payload) => { return modifiedPayload })
app.addHook("onSend", async (request, reply, payload) => { return modifiedPayload })
app.addHook("onResponse", async (request, reply) => {})
app.addHook("onError", async (request, reply, error) => {})
app.addHook("onTimeout", async (request, reply) => {})

// Application lifecycle hooks
app.addHook("onReady", async () => {})
app.addHook("onListen", async () => {})
app.addHook("onClose", async (instance) => {})
app.addHook("preClose", async () => {})
app.addHook("onRoute", (routeOptions) => {})   // sync
app.addHook("onRegister", (instance, opts) => {}) // sync
```

## [Architectural_Laws]
- **Export_Law**: Export plugins as `FastifyPluginAsync`. Use `fastify-plugin` for plugins that should NOT create encapsulation context. Export route schemas as typed const objects.
- **Transformation_Law**: Plugin-based architecture. Each `register()` call creates an encapsulation context. Use type providers (Zod, TypeBox) for schema-to-type inference. Decorators extend instance/request/reply types.
- **Propagation_Law**: Errors handled via `setErrorHandler`. Hooks short-circuit on `reply.send()`. Use `setNotFoundHandler` for 404. Fastify validates request/response schemas by default using Ajv.

## [Syntax_Rules] | [Naming_Conventions]
- camelCase: route handlers, hook names, plugin names
- kebab-case: URL paths, plugin package names
- PascalCase: type interfaces, type providers

## [Prohibited_Patterns]
- NO Express-style `next()` — Fastify uses async/await or reply chaining
- NO `app.use()` for Fastify plugins — use `app.register()` (Express compat via `@fastify/express`)
- NO mutation of raw request/reply outside hooks
- NO `reply.send()` without `return reply` in async handlers

## [Standard_Library_Signatures]
```ts
// Route registration (types/instance.d.ts)
app.get<RouteGeneric>(url: string, opts?: RouteShorthandOptions, handler: RouteHandlerMethod): FastifyInstance
app.post<RouteGeneric>(url: string, opts?, handler): FastifyInstance
app.put<RouteGeneric>(url: string, opts?, handler): FastifyInstance
app.delete<RouteGeneric>(url: string, opts?, handler): FastifyInstance
app.patch<RouteGeneric>(url: string, opts?, handler): FastifyInstance
app.head<RouteGeneric>(url: string, opts?, handler): FastifyInstance
app.options<RouteGeneric>(url: string, opts?, handler): FastifyInstance
app.all<RouteGeneric>(url: string, opts?, handler): FastifyInstance
app.route<RouteGeneric>(opts: RouteOptions): FastifyInstance

// Plugin registration (types/register.d.ts, types/plugin.d.ts)
app.register(plugin: FastifyPluginAsync, opts?: FastifyRegisterOptions): FastifyInstance
app.register(plugin: FastifyPluginCallback, opts?: FastifyRegisterOptions): FastifyInstance

// Decorators (types/instance.d.ts)
app.decorate(name: string, value: any): FastifyInstance
app.decorateRequest(name: string, value: any): FastifyInstance
app.decorateReply(name: string, value: any): FastifyInstance
app.hasDecorator(name: string): boolean
app.hasRequestDecorator(name: string): boolean
app.hasReplyDecorator(name: string): boolean

// Content type parser (types/content-type-parser.d.ts)
app.addContentTypeParser(contentType: string | string[], opts, parser: (req, body, done) => void): void
app.hasContentTypeParser(contentType: string): boolean

// Error handling (types/errors.d.ts)
app.setErrorHandler<TError extends Error>(handler: (error: TError, request: FastifyRequest, reply: FastifyReply) => void): FastifyInstance
app.setNotFoundHandler(handler: (request: FastifyRequest, reply: FastifyReply) => void): FastifyInstance

// Lifecycle
app.listen(opts: FastifyListenOptions): Promise<string>
app.ready(): Promise<FastifyInstance>
app.close(): Promise<undefined>
app.inject(opts): Promise<Response>  // for testing

// Schema management (types/schema.d.ts)
app.addSchema(schema: object): FastifyInstance
app.getSchemas(): Record<string, object>
app.getSchema(schemaId: string): object
```
