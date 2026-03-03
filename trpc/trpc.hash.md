---
Language: tRPC
Version: 11.x
Fidelity: 100% (Physical Disk Reference)
State_ID: BigInt(0x1)
LSP_Discovery_Root: "@root/node_modules/@trpc/server/package.json"
Grammar_Lock: "@root/hashes/grammar/trpc.hash.md"
---

/** [Project].Grammar.tRPC - Linguistic DNA anchor for tRPC 11.x */

## [SDK_Discovery_Map]
/** === @trpc/server (19 definition files, .d.mts) === */
/** @Ref: @root/node_modules/@trpc/server/dist/index.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/http.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/rpc.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/shared.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/observable/index.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/unstable-core-do-not-import.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/unstable-core-do-not-import.d-BxnV2Pug.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/index.d-C_zRYGiu.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/index.d-D4qZxQJh.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/index.d-vq_QHko2.d.mts */
/** === Adapters === */
/** @Ref: @root/node_modules/@trpc/server/dist/adapters/fetch/index.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/adapters/next.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/adapters/next-app-dir.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/adapters/express.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/adapters/fastify/index.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/adapters/standalone.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/adapters/ws.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/adapters/aws-lambda/index.d.mts */
/** @Ref: @root/node_modules/@trpc/server/dist/adapters/node-http/index.d.mts */
/** === @trpc/client (16 definition files, .d.mts) === */
/** @Ref: @root/node_modules/@trpc/client/dist/index.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/links/httpLink.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/links/httpBatchLink.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/links/loggerLink.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/links/splitLink.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/links/wsLink/wsLink.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/unstable-internals.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/types.d-DzHzvxX_.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/httpUtils.d-DCFhYjvc.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/httpBatchLink.d-DONE4mut.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/httpLink.d-kEYW0B3D.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/loggerLink.d-KvQyfaqf.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/splitLink.d-CySNfPDL.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/wsLink.d-BqjtUiqF.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/subscriptions.d-Dlr1nWGD.d.mts */
/** @Ref: @root/node_modules/@trpc/client/dist/unstable-internals.d-BOmV7EK1.d.mts */

## [SDK_Imports / Namespaces]
```ts
// Server
import { initTRPC, TRPCError } from "@trpc/server"
import type { inferRouterInputs, inferRouterOutputs, AnyRouter, CreateRouterInner, ProcedureBuilder, ProcedureType, ProcedureParams, MiddlewareBuilder, MiddlewareFunction } from "@trpc/server"
import { fetchRequestHandler } from "@trpc/server/adapters/fetch"
import { createNextApiHandler } from "@trpc/server/adapters/next"
import { observable } from "@trpc/server/observable"

// Client
import { createTRPCClient, httpBatchLink, httpLink, loggerLink, splitLink, wsLink, TRPCClientError } from "@trpc/client"
import type { CreateTRPCClient, TRPCLink } from "@trpc/client"

// React integration (via @trpc/react-query or @trpc/tanstack-react-query)
import { createTRPCReact } from "@trpc/react-query"
```

## [Core_Primitives]
```ts
// Server initialization (index.d.mts)
const t = initTRPC.context<TContext>().create({
  errorFormatter?: ({ shape, error }) => ({ ...shape, data: { ...shape.data, custom: error.cause } }),
  transformer?: SuperJSON,
  isDev?: boolean,
})

// Building blocks
const router = t.router
const publicProcedure = t.procedure
const middleware = t.middleware
const mergeRouters = t.mergeRouters
const createCallerFactory = t.createCallerFactory

// Procedure chain (index.d.mts - ProcedureBuilder)
t.procedure
  .input(z.object({ ... }))          // ZodType | custom validator
  .output(z.object({ ... }))         // optional output validation
  .use(middleware)                     // middleware (can be chained)
  .meta({ ... })                      // procedure metadata
  .query(async ({ input, ctx }) => {}) // read operation
  .mutation(async ({ input, ctx }) => {}) // write operation
  .subscription(async function*({ input, ctx }) { yield data }) // real-time

// Router definition
const appRouter = router({
  user: router({
    getById: publicProcedure.input(z.object({ id: z.string() })).query(async ({ input, ctx }) => { ... }),
    create: publicProcedure.input(z.object({ name: z.string() })).mutation(async ({ input, ctx }) => { ... }),
    onUpdate: publicProcedure.subscription(async function*() { ... }),
  }),
})
type AppRouter = typeof appRouter

// Type inference
type RouterInputs = inferRouterInputs<AppRouter>
type RouterOutputs = inferRouterOutputs<AppRouter>

// Context
type TContext = { db: PrismaClient; session: Session | null }
const createContext = async (opts: CreateNextContextOptions) => ({ db: prisma, session: await getSession(opts) })

// Middleware (chaining)
const isAuthed = middleware(async ({ ctx, next }) => {
  if (!ctx.session) throw new TRPCError({ code: "UNAUTHORIZED" })
  return next({ ctx: { ...ctx, session: ctx.session } })  // narrows ctx type
})
const protectedProcedure = publicProcedure.use(isAuthed)
```

## [Architectural_Laws]
- **Export_Law**: Export `appRouter` type (`type AppRouter = typeof appRouter`) for client-side type inference. Export context creator. Export procedure helpers (`publicProcedure`, `protectedProcedure`).
- **Transformation_Law**: Full type inference from server to client — NO codegen needed. Input validated by Zod schemas. Output optionally validated. Middleware narrows context types via `next({ ctx })`.
- **Propagation_Law**: Errors as `TRPCError` with HTTP-aligned codes. Client receives typed errors via `TRPCClientError`. Use `errorFormatter` for custom error shapes. Subscriptions use async generators or observables.

## [Syntax_Rules] | [Naming_Conventions]
- camelCase: procedure names (`getById`, `createUser`)
- Nested routers: `appRouter.user.getById` → `trpc.user.getById`
- Procedures: `query` for reads, `mutation` for writes, `subscription` for real-time
- Context: `ctx` parameter in resolvers, narrowed by middleware

## [Prohibited_Patterns]
- NO direct `appRouter` calls from client — use typed client or `createCaller`
- NO `any` in input/output schemas — use Zod for type safety
- NO context mutation — return new context from middleware via `next({ ctx })`
- NO subscription without proper cleanup — use async generator `return` or observable teardown

## [Error_Modeling]
```ts
// TRPCError (server)
class TRPCError extends Error {
  readonly code: TRPC_ERROR_CODE_KEY
  readonly cause?: unknown
}

// Error codes (HTTP-mapped):
"PARSE_ERROR"           // 400
"BAD_REQUEST"           // 400
"NOT_FOUND"             // 404
"UNAUTHORIZED"          // 401
"FORBIDDEN"             // 403
"INTERNAL_SERVER_ERROR" // 500
"TIMEOUT"               // 408
"CONFLICT"              // 409
"PRECONDITION_FAILED"   // 412
"PAYLOAD_TOO_LARGE"     // 413
"UNPROCESSABLE_CONTENT" // 422
"TOO_MANY_REQUESTS"     // 429
"CLIENT_CLOSED_REQUEST" // 499
"METHOD_NOT_SUPPORTED"  // 405
"NOT_IMPLEMENTED"       // 501

// TRPCClientError (client)
class TRPCClientError<TRouter> extends Error {
  readonly data?: TRouter extends AnyRouter ? inferRouterError<TRouter>['data'] : never
  readonly shape?: TRouter extends AnyRouter ? inferRouterError<TRouter> : never
}
```

## [Standard_Library_Signatures]
```ts
// Client creation
const client = createTRPCClient<AppRouter>({ links: [httpBatchLink({ url: "/api/trpc" })] })

// Client calls (fully typed)
const user = await client.user.getById.query({ id: "123" })
const newUser = await client.user.create.mutate({ name: "Alice" })
const sub = client.user.onUpdate.subscribe(undefined, { onData(data) {}, onError(err) {} })

// Links (client/dist/links/)
httpLink({ url: string, headers?: () => Record<string, string> })
httpBatchLink({ url: string, maxURLLength?: number, headers?: () => Record<string, string> })
loggerLink({ enabled?: (opts) => boolean, colorMode?: "ansi" | "css" })
splitLink({ condition: (op) => boolean, true: TRPCLink, false: TRPCLink })
wsLink({ client: WebSocket | (() => WebSocket) })

// Adapters
fetchRequestHandler({ endpoint: string, req: Request, router: AnyRouter, createContext })
createNextApiHandler({ router: AnyRouter, createContext })

// React Query integration
const trpc = createTRPCReact<AppRouter>()
// hooks: trpc.user.getById.useQuery({ id }), trpc.user.create.useMutation()
// trpc.useQueries(), trpc.useSuspenseQuery()

// Server caller (for testing / server-side calls)
const createCaller = createCallerFactory(appRouter)
const caller = createCaller(createContext)
const user = await caller.user.getById({ id: "123" })
```
