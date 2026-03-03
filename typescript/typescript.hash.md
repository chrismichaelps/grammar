---
Language: TypeScript
Version: 5.9.x
Fidelity: 100% (Physical Disk Reference)
State_ID: BigInt(0x1)
LSP_Discovery_Root: "@root/node_modules/typescript/package.json"
Grammar_Lock: "@root/hashes/grammar/typescript.hash.md"
---

/** [Project].Grammar.TypeScript - Linguistic DNA anchor for TypeScript 5.9.x */

## [SDK_Discovery_Map]
/** === Core Lib Files (50+ declarations) === */
/** @Ref: @root/node_modules/typescript/lib/lib.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es5.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.collection.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.core.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.generator.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.iterable.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.promise.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.proxy.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.reflect.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.symbol.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2015.symbol.wellknown.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2016.array.include.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2017.object.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2017.string.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2017.typedarrays.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2018.asyncgenerator.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2018.asynciterable.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2018.promise.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2018.regexp.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2019.array.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2019.object.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2019.string.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2020.bigint.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2020.promise.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2020.string.matchall.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2021.promise.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2021.string.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2021.weakref.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2022.array.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2022.error.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2022.object.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2023.array.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2023.collection.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2024.arraybuffer.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.es2024.promise.d.ts */
/** === Decorator System === */
/** @Ref: @root/node_modules/typescript/lib/lib.decorators.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.decorators.legacy.d.ts */
/** === DOM === */
/** @Ref: @root/node_modules/typescript/lib/lib.dom.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.dom.iterable.d.ts */
/** @Ref: @root/node_modules/typescript/lib/lib.dom.asynciterable.d.ts */

## [SDK_Imports / Namespaces]
```ts
// TypeScript is a language, not a library. No import needed.
// Configured via tsconfig.json "lib" array:
// "lib": ["ES2024", "DOM", "DOM.Iterable"]
```

## [Core_Primitives]
```ts
// Primitive types (lib.es5.d.ts)
string | number | boolean | bigint | symbol | undefined | null | void | never | unknown | any | object

// Utility types (lib.es5.d.ts)
Partial<T>           // all properties optional
Required<T>          // all properties required
Readonly<T>          // all properties readonly
Record<K, V>         // { [P in K]: V }
Pick<T, K>           // subset of properties
Omit<T, K>           // exclude properties
Exclude<T, U>        // exclude from union
Extract<T, U>        // extract from union
NonNullable<T>       // remove null | undefined
Parameters<T>        // function parameter types as tuple
ReturnType<T>        // function return type
ConstructorParameters<T> // constructor params
InstanceType<T>      // instance type of constructor
Awaited<T>           // unwrap Promise recursively
ThisParameterType<T> // extract 'this' param type
OmitThisParameter<T> // remove 'this' param
NoInfer<T>           // prevent inference site (TS 5.4+)
PropertyKey          // string | number | symbol

// Intrinsic string manipulation (TS 4.1+)
Uppercase<S>  Lowercase<S>  Capitalize<S>  Uncapitalize<S>

// Template literal types
type Route = `/${string}`
type EventName = `on${Capitalize<string>}`

// Satisfies operator (TS 4.9+)
const config = { ... } satisfies Config

// Iterator/Iterable protocol (lib.es2015.iterable.d.ts)
interface Iterator<T, TReturn = any, TNext = any>  // next(), return(), throw()
interface Iterable<T>                                // [Symbol.iterator]()
interface IterableIterator<T>                        // extends both
interface IteratorObject<T>                          // runtime intrinsic

// Promise (lib.es2015.promise.d.ts)
new Promise<T>(executor: (resolve, reject) => void): Promise<T>
Promise.all<T>(values): Promise<Awaited<T>[]>
Promise.race<T>(values): Promise<Awaited<T>>
Promise.allSettled(values): Promise<PromiseSettledResult<T>[]>
Promise.any(values): Promise<Awaited<T>>           // ES2021
Promise.withResolvers<T>(): { promise, resolve, reject }  // ES2024

// Collections (lib.es2015.collection.d.ts)
Map<K, V>     WeakMap<K, V>
Set<T>        WeakSet<T>
WeakRef<T>    FinalizationRegistry<T>  // ES2021

// Stage 3 Decorators (lib.decorators.d.ts) — NOT legacy
type DecoratorContext = ClassDecoratorContext | ClassMemberDecoratorContext
type ClassMemberDecoratorContext =
  | ClassMethodDecoratorContext<This, Value>   // kind: "method"
  | ClassGetterDecoratorContext<This, Value>   // kind: "getter"
  | ClassSetterDecoratorContext<This, Value>   // kind: "setter"
  | ClassFieldDecoratorContext<This, Value>    // kind: "field"
  | ClassAccessorDecoratorContext<This, Value> // kind: "accessor"

// Each context has: kind, name, static, private, access, addInitializer(), metadata

// @deprecated Legacy Decorators (lib.decorators.legacy.d.ts)
// ClassDecorator, MethodDecorator, ParameterDecorator, PropertyDecorator
// Still used by NestJS, Angular. Requires "experimentalDecorators": true
```

## [Architectural_Laws]
- **Export_Law**: Use named exports exclusively. Re-export via barrel `index.ts`. Default exports only for React components and Next.js pages.
- **Transformation_Law**: Use discriminated unions over inheritance. Prefer `unknown` over `any`. Narrow via user-defined type guards: `(val): val is T =>`.
- **Propagation_Law**: Errors as values (Result pattern) or typed `throw`. Use `Error.cause` (ES2022) for error chaining. Never `catch(e: any)` — use `catch(e: unknown)` and narrow.

## [Syntax_Rules] | [Naming_Conventions]
- PascalCase: types, interfaces, classes, enums
- camelCase: functions, variables, methods, properties
- UPPER_CASE: const enums, true constants
- `T` prefix for generic type parameters: `TData`, `TError` (or single letter `T`, `K`, `V`)
- `I` prefix: NEVER (anti-pattern in modern TS)
- `.ts` / `.tsx` extensions
- `as const` for literal inference
- `readonly` on arrays/tuples when immutable: `readonly string[]`

## [Prohibited_Patterns]
- NO `any` — use `unknown` and narrow
- NO `enum` in new code — use `as const` objects with `typeof` for unions
- NO non-null assertion `!` — use proper narrowing or optional chaining
- NO `namespace` — use ES modules
- NO `/// <reference>` — use `import type`
- NO `@ts-ignore` — use `@ts-expect-error` with description
- NO `Function` type — use specific signatures `(...args: ...) => ReturnType`
- NO `Object` / `String` / `Number` / `Boolean` wrappers — use lowercase primitives

## [Deprecated_Definitions]
```ts
// @deprecated lib.es5.d.ts
escape(string: string): string    // use encodeURIComponent
unescape(string: string): string  // use decodeURIComponent
String.prototype.substr(from, length) // use slice() or substring()

// @deprecated Legacy decorators (still functional with flag)
type ClassDecorator = <TFunction>(target: TFunction) => TFunction | void
type MethodDecorator = <T>(target, propertyKey, descriptor: TypedPropertyDescriptor<T>) => TypedPropertyDescriptor<T> | void
type ParameterDecorator = (target, propertyKey, parameterIndex: number) => void
type PropertyDecorator = (target, propertyKey) => void
```

## [Standard_Library_Signatures]
```ts
// Object (lib.es5.d.ts — 4602 lines)
Object.keys(o: object): string[]
Object.values<T>(o: Record<string, T>): T[]           // ES2017
Object.entries<T>(o: Record<string, T>): [string, T][] // ES2017
Object.fromEntries<T>(entries: Iterable<[string, T]>): Record<string, T> // ES2019
Object.hasOwn(o: object, key: PropertyKey): boolean    // ES2022
Object.assign<T, U>(target: T, source: U): T & U
Object.freeze<T>(o: T): Readonly<T>
Object.groupBy<K, T>(items: Iterable<T>, keySelector: (item: T) => K): Record<K, T[]> // ES2024

// Array (lib.es5.d.ts + es2015+ additions)
Array.from<T>(iterable: Iterable<T>): T[]
Array.isArray(arg: any): arg is any[]
Array.prototype.at(index: number): T | undefined       // ES2022
Array.prototype.findLast(predicate): T | undefined      // ES2023
Array.prototype.findLastIndex(predicate): number        // ES2023
Array.prototype.toSorted(compareFn?): T[]               // ES2023, non-mutating
Array.prototype.toReversed(): T[]                       // ES2023, non-mutating
Array.prototype.toSpliced(start, deleteCount, ...items): T[] // ES2023
Array.prototype.with(index, value): T[]                 // ES2023
Array.prototype.flatMap<U>(callback): U[]               // ES2019
Array.prototype.flat(depth?): any[]                     // ES2019
Array.prototype.includes(value): boolean                // ES2016

// String (lib.es5.d.ts + es2015+ additions)
String.prototype.startsWith(searchString, position?): boolean // ES2015
String.prototype.endsWith(searchString, position?): boolean   // ES2015
String.prototype.includes(searchString, position?): boolean   // ES2015
String.prototype.padStart(maxLength, fillString?): string     // ES2017
String.prototype.padEnd(maxLength, fillString?): string       // ES2017
String.prototype.trimStart(): string                          // ES2019
String.prototype.trimEnd(): string                            // ES2019
String.prototype.replaceAll(searchValue, replaceValue): string // ES2021
String.prototype.matchAll(regexp): IterableIterator<RegExpMatchArray> // ES2020

// Error (lib.es5.d.ts + es2022)
interface Error { name: string; message: string; stack?: string; cause?: unknown }
class AggregateError extends Error { errors: any[] }    // ES2021
// Error.cause: unknown — pass via new Error("msg", { cause: originalError }) // ES2022

// Structured clone, JSON
structuredClone<T>(value: T): T                         // ES2024
JSON.parse(text: string, reviver?): any
JSON.stringify(value: any, replacer?, space?): string

// Math (lib.es5.d.ts — all methods)
Math.abs, Math.ceil, Math.floor, Math.round, Math.max, Math.min, Math.pow, Math.random
Math.trunc(x): number    // ES2015
Math.sign(x): number     // ES2015
Math.cbrt(x): number     // ES2015
Math.log2(x): number     // ES2015
Math.log10(x): number    // ES2015
Math.fround(x): number   // ES2015
Math.clz32(x): number    // ES2015
Math.imul(a, b): number  // ES2015
```
