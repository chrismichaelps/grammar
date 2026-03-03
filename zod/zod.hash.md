---
Language: Zod
Version: 4.3.x
Fidelity: 100% (Physical Disk Reference)
State_ID: BigInt(0x1)
LSP_Discovery_Root: "@root/node_modules/zod/package.json"
Grammar_Lock: "@root/hashes/grammar/zod.hash.md"
---

/** [Project].Grammar.Zod - Linguistic DNA anchor for Zod 4.x */

## [SDK_Discovery_Map]
/** === Entry Points === */
/** @Ref: @root/node_modules/zod/index.d.ts */
/** @Ref: @root/node_modules/zod/v4/index.d.ts */
/** === v4 Classic (default API) === */
/** @Ref: @root/node_modules/zod/v4/classic/index.d.ts */
/** @Ref: @root/node_modules/zod/v4/classic/external.d.ts */
/** @Ref: @root/node_modules/zod/v4/classic/schemas.d.ts */
/** @Ref: @root/node_modules/zod/v4/classic/parse.d.ts */
/** @Ref: @root/node_modules/zod/v4/classic/checks.d.ts */
/** @Ref: @root/node_modules/zod/v4/classic/coerce.d.ts */
/** @Ref: @root/node_modules/zod/v4/classic/compat.d.ts */
/** @Ref: @root/node_modules/zod/v4/classic/errors.d.ts */
/** @Ref: @root/node_modules/zod/v4/classic/from-json-schema.d.ts */
/** @Ref: @root/node_modules/zod/v4/classic/iso.d.ts */
/** === v4 Core (internal engine) === */
/** @Ref: @root/node_modules/zod/v4/core/core.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/schemas.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/api.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/checks.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/errors.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/parse.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/regexes.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/registries.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/standard-schema.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/json-schema.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/json-schema-generator.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/to-json-schema.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/util.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/doc.d.ts */
/** @Ref: @root/node_modules/zod/v4/core/versions.d.ts */
/** === v4 Mini (tree-shakeable alternative) === */
/** @Ref: @root/node_modules/zod/v4/mini/index.d.ts */
/** @Ref: @root/node_modules/zod/v4/mini/schemas.d.ts */
/** @Ref: @root/node_modules/zod/v4/mini/parse.d.ts */
/** @Ref: @root/node_modules/zod/v4/mini/checks.d.ts */
/** @Ref: @root/node_modules/zod/v4/mini/coerce.d.ts */
/** @Ref: @root/node_modules/zod/v4/mini/external.d.ts */
/** @Ref: @root/node_modules/zod/v4/mini/iso.d.ts */
/** === v3 Legacy (backward compat) === */
/** @Ref: @root/node_modules/zod/v3/index.d.ts */
/** @Ref: @root/node_modules/zod/v3/types.d.ts */
/** @Ref: @root/node_modules/zod/v3/ZodError.d.ts */
/** @Ref: @root/node_modules/zod/v3/external.d.ts */
/** @Ref: @root/node_modules/zod/v3/errors.d.ts */
/** @Ref: @root/node_modules/zod/v3/standard-schema.d.ts */
/** @Ref: @root/node_modules/zod/v3/helpers/parseUtil.d.ts */
/** @Ref: @root/node_modules/zod/v3/helpers/enumUtil.d.ts */
/** @Ref: @root/node_modules/zod/v3/helpers/util.d.ts */
/** === Locales (40+ language packs) === */
/** @Ref: @root/node_modules/zod/v4/locales/en.d.ts */
/** @Ref: @root/node_modules/zod/locales/index.d.ts */
/** @Ref: @root/node_modules/zod/v4-mini/index.d.ts */
/** @Ref: @root/node_modules/zod/mini/index.d.ts */

## [SDK_Imports / Namespaces]
```ts
// v4 Classic (default)
import { z } from "zod"
import type { ZodType, ZodObject, ZodString, ZodNumber, ZodBoolean, ZodArray, ZodEnum,
  ZodUnion, ZodDiscriminatedUnion, ZodIntersection, ZodTuple, ZodRecord, ZodMap,
  ZodSet, ZodLazy, ZodOptional, ZodNullable, ZodDefault, ZodPipeline, ZodEffects,
  ZodNativeEnum, ZodLiteral, ZodBranded, ZodCatch, ZodReadonly, ZodTemplateLiteral,
  infer as ZodInfer } from "zod"
import type { ZodError, ZodIssue, ZodIssueCode, ZodFormattedError } from "zod"

// v4 Mini (tree-shakeable, for bundles)
import { z } from "zod/v4-mini"

// v3 compat (deprecated but functional)
import { z } from "zod/v3"
```

## [Core_Primitives]
```ts
// Schema factories (v4/classic/schemas.d.ts — 740+ lines)
z.string()      z.number()      z.bigint()     z.boolean()
z.date()        z.symbol()      z.undefined()  z.null()
z.void()        z.any()         z.unknown()    z.never()
z.nan()         z.literal(value)

// Composite schema types
z.object({ key: z.string() })         // ZodObject
z.array(z.string())                    // ZodArray
z.tuple([z.string(), z.number()])      // ZodTuple
z.union([z.string(), z.number()])      // ZodUnion
z.discriminatedUnion("type", [...])    // ZodDiscriminatedUnion
z.intersection(schemaA, schemaB)       // ZodIntersection
z.record(z.string(), z.number())       // ZodRecord
z.map(z.string(), z.number())          // ZodMap
z.set(z.string())                      // ZodSet
z.enum(["A", "B", "C"])               // ZodEnum
z.nativeEnum(TsEnum)                   // ZodNativeEnum
z.promise(z.string())                  // ZodPromise
z.function(args, returns)              // ZodFunction
z.lazy(() => schema)                   // ZodLazy (recursive)
z.templateLiteral([z.literal("prefix-"), z.string()]) // ZodTemplateLiteral (v4)

// Type inference (THE core pattern)
type User = z.infer<typeof UserSchema>
type UserInput = z.input<typeof UserSchema>   // before transforms
type UserOutput = z.output<typeof UserSchema>  // after transforms

// String checks (v4/classic/checks.d.ts, v4/core/regexes.d.ts)
z.string().min(1).max(255).email().url().uuid().cuid().cuid2()
  .ulid().ip().cidr().regex(/pattern/).trim().toLowerCase().toUpperCase()
  .startsWith("prefix").endsWith("suffix").includes("substr")
  .datetime().date().time().duration().base64().jwt()
  .nanoid().emoji().iso()

// Number checks
z.number().min(0).max(100).int().positive().negative()
  .nonnegative().nonpositive().finite().safe().multipleOf(5)

// Coercion (v4/classic/coerce.d.ts)
z.coerce.string()   z.coerce.number()   z.coerce.boolean()
z.coerce.bigint()   z.coerce.date()
```

## [Architectural_Laws]
- **Export_Law**: Export schemas as `const` with PascalCase suffix `Schema`. Export inferred types alongside: `type User = z.infer<typeof UserSchema>`.
- **Transformation_Law**: Use `.transform()` for data mapping, `.pipe()` for schema-to-schema composition (ZodPipeline). Use `.refine()` / `.superRefine()` for custom validation with type narrowing.
- **Propagation_Law**: `.safeParse()` returns `{ success, data } | { success, error }` — never throws. `.parse()` throws `ZodError`. Use `ZodError.flatten()` for form-friendly formatting. Use `ZodError.format()` for nested access.

## [Syntax_Rules] | [Naming_Conventions]
- PascalCase + `Schema` suffix: `UserSchema`, `CreatePostSchema`
- PascalCase for inferred types: `type User = z.infer<typeof UserSchema>`
- camelCase: validation functions, parse calls
- Chain checks fluently: `z.string().min(1).email()`
- `z.` prefix: all schema factories

## [Prohibited_Patterns]
- NO manual type definitions when schema exists — use `z.infer<typeof Schema>` always
- NO `.parse()` without try/catch — use `.safeParse()` for safe path
- NO runtime `instanceof` checks on schemas — use `schema.safeParse()` for validation
- NO v3 API in new code — use v4 classic or v4-mini
- NO `z.any()` in production schemas — use `z.unknown()` and narrow

## [Deprecated_Definitions]
```ts
// v3 API — still functional via "zod/v3" import but superseded by v4
// v3 ZodError structure differs from v4
// v3 .describe() — replaced by v4 registries & doc system
// v3 helper utilities in zod/v3/helpers/ — internals, do not import directly
```

## [Standard_Library_Signatures]
```ts
// Parsing (v4/classic/parse.d.ts)
schema.parse(data: unknown): T                          // throws ZodError
schema.safeParse(data: unknown): SafeParseResult<T>     // never throws
schema.parseAsync(data: unknown): Promise<T>
schema.safeParseAsync(data: unknown): Promise<SafeParseResult<T>>

// Modifiers
schema.optional(): ZodOptional<T>        // T | undefined
schema.nullable(): ZodNullable<T>        // T | null
schema.nullish(): ZodNullable<ZodOptional<T>>  // T | null | undefined
schema.default(value): ZodDefault<T>
schema.catch(value): ZodCatch<T>         // fallback on error
schema.readonly(): ZodReadonly<T>
schema.brand<B>(): ZodBranded<T, B>      // nominal typing
schema.pipe(otherSchema): ZodPipeline    // chain schemas

// Object methods
z.object({}).partial()                   // all optional
z.object({}).required()                  // all required
z.object({}).pick({ key: true })         // subset
z.object({}).omit({ key: true })         // exclude
z.object({}).extend({ newKey: z.number() })
z.object({}).merge(otherObjectSchema)
z.object({}).keyof()                     // ZodEnum from keys
z.object({}).strict()                    // no unrecognized keys (error)
z.object({}).strip()                     // strip unknown keys (default)
z.object({}).passthrough()               // pass unknown keys through

// Transforms & Refinements
schema.transform(val => transformed)
schema.refine(val => boolean, { message })
schema.superRefine((val, ctx) => { ctx.addIssue(...) })

// JSON Schema (v4/core/to-json-schema.d.ts, v4/core/json-schema.d.ts)
z.toJSONSchema(schema): JSONSchema       // convert to JSON Schema
z.fromJSONSchema(jsonSchema): ZodType    // convert from JSON Schema (v4/classic/from-json-schema.d.ts)

// Registries (v4/core/registries.d.ts)
const registry = z.registry<z.ZodType, { description: string }>()
registry.register(schema, metadata)
registry.get(schema)

// Standard Schema (v4/core/standard-schema.d.ts)
// Zod v4 implements the Standard Schema interface for interop
```

## [Error_Modeling]
```ts
// ZodError (v4/classic/errors.d.ts, v4/core/errors.d.ts)
class ZodError extends Error {
  issues: ZodIssue[]
  format(): ZodFormattedError
  flatten(): { formErrors: string[]; fieldErrors: Record<string, string[]> }
}

// ZodIssue.code values:
"invalid_type" | "unrecognized_keys" | "invalid_union" | "invalid_union_discriminator" |
"invalid_enum_value" | "invalid_arguments" | "invalid_return_type" | "invalid_date" |
"custom" | "invalid_intersection_types" | "not_multiple_of" | "not_finite" |
"invalid_string" | "too_small" | "too_big" | "invalid_literal"
```
