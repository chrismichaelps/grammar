---
Language: TanStack React Query
Version: 5.x
Fidelity: 100% (Physical Disk Reference)
State_ID: BigInt(0x1)
LSP_Discovery_Root: "@root/node_modules/@tanstack/react-query/package.json"
Grammar_Lock: "@root/hashes/grammar/tanstack-react-query.hash.md"
---

/** [Project].Grammar.TanStackReactQuery - Linguistic DNA anchor for TanStack React Query 5.x */

## [SDK_Discovery_Map]
/** === Modern Build (entry point + 23 module files) === */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/index.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/types.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useInfiniteQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useMutation.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useQueries.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useSuspenseQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useSuspenseInfiniteQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useSuspenseQueries.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/usePrefetchQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/usePrefetchInfiniteQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useIsFetching.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useMutationState.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/useBaseQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/queryOptions.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/infiniteQueryOptions.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/mutationOptions.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/suspense.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/errorBoundaryUtils.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/QueryClientProvider.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/QueryErrorResetBoundary.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/HydrationBoundary.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/modern/IsRestoringProvider.d.ts */
/** === Legacy Build (backward compat, same modules) === */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/index.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/types.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useInfiniteQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useMutation.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useQueries.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useSuspenseQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useSuspenseInfiniteQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useSuspenseQueries.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/usePrefetchQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/usePrefetchInfiniteQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useIsFetching.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useMutationState.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/useBaseQuery.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/queryOptions.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/infiniteQueryOptions.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/mutationOptions.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/suspense.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/errorBoundaryUtils.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/QueryClientProvider.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/QueryErrorResetBoundary.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/HydrationBoundary.d.ts */
/** @Ref: @root/node_modules/@tanstack/react-query/build/legacy/IsRestoringProvider.d.ts */

## [SDK_Imports / Namespaces]
```ts
// Re-exports from @tanstack/query-core (via modern/index.d.ts L1)
import { QueryClient, QueryCache, MutationCache, QueryObserver, InfiniteQueryObserver, MutationObserver, QueriesObserver, focusManager, onlineManager, notifyManager, hashKey, keepPreviousData, skipToken } from "@tanstack/react-query"
import type { QueryKey, QueryFunction, QueryFilters, MutationFilters, QueryOptions, MutationOptions, InfiniteData, DefaultError, QueryMeta, MutationMeta, Updater, Hydrate, DehydratedState } from "@tanstack/react-query"

// React hooks (modern/index.d.ts L2-22)
import { useQuery, useInfiniteQuery, useMutation, useQueries, useSuspenseQuery, useSuspenseInfiniteQuery, useSuspenseQueries, usePrefetchQuery, usePrefetchInfiniteQuery, useIsFetching, useMutationState, useQueryClient } from "@tanstack/react-query"

// Option factories
import { queryOptions, infiniteQueryOptions, mutationOptions } from "@tanstack/react-query"

// Type helpers (modern/types.d.ts)
import type { UseQueryOptions, UseQueryResult, DefinedUseQueryResult, UseInfiniteQueryOptions, UseInfiniteQueryResult, DefinedUseInfiniteQueryResult, UseMutationOptions, UseMutationResult, UseSuspenseQueryOptions, UseSuspenseQueryResult, UseSuspenseInfiniteQueryOptions, UseSuspenseInfiniteQueryResult, UseMutateFunction, UseMutateAsyncFunction, UsePrefetchQueryOptions, QueriesOptions, QueriesResults, SuspenseQueriesOptions, SuspenseQueriesResults } from "@tanstack/react-query"

// Components
import { QueryClientProvider, HydrationBoundary, QueryErrorResetBoundary } from "@tanstack/react-query"
import type { QueryClientProviderProps, HydrationBoundaryProps, QueryErrorResetBoundaryProps } from "@tanstack/react-query"
```

## [Core_Primitives]
```ts
// QueryClient
const queryClient = new QueryClient({
  defaultOptions?: {
    queries?: { staleTime?, gcTime?, retry?, retryDelay?, refetchOnWindowFocus?, refetchOnReconnect?, refetchOnMount?, refetchInterval?, networkMode? },
    mutations?: { retry?, retryDelay?, networkMode?, gcTime? },
  }
})

// Query key pattern (THE foundational concept)
type QueryKey = readonly unknown[]
// Convention: ["entity", "action", { filters }]
// e.g., ["users", "list", { role: "admin" }]
// e.g., ["users", "detail", userId]

// queryOptions factory (modern/queryOptions.d.ts)
const userQueryOptions = (userId: string) => queryOptions({
  queryKey: ["users", "detail", userId] as const,
  queryFn: () => fetchUser(userId),
  staleTime: 5 * 60 * 1000,
})
// Type helpers from queryOptions:
type DefinedInitialDataOptions   // when initialData is provided
type UndefinedInitialDataOptions // when initialData is NOT provided
type UnusedSkipTokenOptions      // when skipToken is not used

// infiniteQueryOptions factory (modern/infiniteQueryOptions.d.ts)
const postsInfiniteOptions = infiniteQueryOptions({
  queryKey: ["posts", "infinite"],
  queryFn: ({ pageParam }) => fetchPosts(pageParam),
  initialPageParam: 0,
  getNextPageParam: (lastPage, pages) => lastPage.nextCursor,
  getPreviousPageParam: (firstPage) => firstPage.prevCursor,
})

// mutationOptions factory (modern/mutationOptions.d.ts)
const createUserMutation = mutationOptions({
  mutationFn: (data: CreateUserInput) => createUser(data),
  onSuccess: (data, variables, context) => { queryClient.invalidateQueries({ queryKey: ["users"] }) },
})
```

## [Hooks_API]
```ts
// useQuery (modern/useQuery.d.ts)
const { data, error, isLoading, isPending, isFetching, isError, isSuccess, isStale, status, fetchStatus, refetch, dataUpdatedAt, errorUpdatedAt, failureCount, failureReason } = useQuery({
  queryKey: QueryKey,
  queryFn: QueryFunction<TData, TQueryKey>,
  enabled?: boolean,
  staleTime?: number,                    // default: 0
  gcTime?: number,                       // default: 5min (was cacheTime in v4)
  refetchOnWindowFocus?: boolean | "always",
  refetchOnReconnect?: boolean | "always",
  refetchOnMount?: boolean | "always",
  refetchInterval?: number | false | ((query) => number | false),
  retry?: boolean | number | ((failureCount, error) => boolean),
  retryDelay?: number | ((attemptIndex, error) => number),
  select?: (data: TData) => TSelected,
  initialData?: TData | (() => TData),
  placeholderData?: TData | ((previousData, previousQuery) => TData) | typeof keepPreviousData,
  networkMode?: "online" | "always" | "offlineFirst",
  meta?: QueryMeta,
  throwOnError?: boolean | ((error, query) => boolean),
})

// useInfiniteQuery (modern/useInfiniteQuery.d.ts)
const { data, fetchNextPage, fetchPreviousPage, hasNextPage, hasPreviousPage, isFetchingNextPage, isFetchingPreviousPage, ... } = useInfiniteQuery({
  ...queryOptions,
  initialPageParam: TPageParam,
  getNextPageParam: (lastPage, allPages, lastPageParam, allPageParams) => TPageParam | undefined | null,
  getPreviousPageParam?: (firstPage, allPages, firstPageParam, allPageParams) => TPageParam | undefined | null,
  maxPages?: number,
})
// data.pages: TData[]        data.pageParams: TPageParam[]

// useMutation (modern/useMutation.d.ts)
const { mutate, mutateAsync, data, error, isIdle, isPending, isSuccess, isError, reset, variables, context, submittedAt, failureCount } = useMutation({
  mutationFn: (variables: TVariables) => Promise<TData>,
  mutationKey?: MutationKey,
  onMutate?: (variables) => Promise<TContext> | TContext,    // optimistic update
  onSuccess?: (data, variables, context) => void,
  onError?: (error, variables, context) => void,
  onSettled?: (data, error, variables, context) => void,
  retry?: number | boolean,
  gcTime?: number,
  meta?: MutationMeta,
  throwOnError?: boolean,
})

// useSuspenseQuery (modern/useSuspenseQuery.d.ts) — data is ALWAYS defined
const { data } = useSuspenseQuery({ queryKey, queryFn })
// No isLoading, isPending (Suspense handles loading state)

// useQueries (modern/useQueries.d.ts) — parallel queries
const results = useQueries({ queries: [queryOptions1, queryOptions2, queryOptions3], combine?: (results) => combinedResult })

// usePrefetchQuery (modern/usePrefetchQuery.d.ts)
usePrefetchQuery({ queryKey, queryFn, staleTime })  // triggers prefetch during render

// useIsFetching (modern/useIsFetching.d.ts)
const fetchingCount = useIsFetching(filters?: QueryFilters)  // number of active fetches

// useMutationState (modern/useMutationState.d.ts)
const mutations = useMutationState({ filters?: MutationFilters, select?: (mutation) => TResult })
const isMutating = useIsMutating(filters?: MutationFilters)

// useQueryClient (modern/QueryClientProvider.d.ts)
const queryClient = useQueryClient()
```

## [Architectural_Laws]
- **Export_Law**: Define query options outside components using `queryOptions()` factory. Export query keys as const arrays. Export mutation options using `mutationOptions()` factory.
- **Transformation_Law**: Stale-while-revalidate by default. Data caches are de-duplicated by query key. Use `select` for derived data. Use `placeholderData: keepPreviousData` for pagination.
- **Propagation_Law**: Use `useSuspenseQuery` with Suspense boundaries. Use `QueryErrorResetBoundary` with Error boundaries. Use `onError` callbacks in mutations. Use `throwOnError` to bubble to error boundaries.

## [Standard_Library_Signatures]
```ts
// QueryClient methods (from @tanstack/query-core)
queryClient.invalidateQueries({ queryKey?, exact?, predicate?, type?, refetchType? }): Promise<void>
queryClient.refetchQueries({ queryKey?, exact?, predicate?, type? }): Promise<void>
queryClient.cancelQueries({ queryKey?, exact?, predicate? }): Promise<void>
queryClient.removeQueries({ queryKey?, exact?, predicate? }): void
queryClient.resetQueries({ queryKey?, exact?, predicate? }): Promise<void>
queryClient.getQueryData<T>(queryKey: QueryKey): T | undefined
queryClient.setQueryData<T>(queryKey: QueryKey, updater: T | ((old: T | undefined) => T)): T
queryClient.getQueriesData<T>(filters: QueryFilters): [QueryKey, T | undefined][]
queryClient.setQueriesData<T>(filters: QueryFilters, updater: Updater<T | undefined, T>): [QueryKey, T | undefined][]
queryClient.getQueryState(queryKey: QueryKey): QueryState | undefined
queryClient.ensureQueryData(options: QueryOptions): Promise<TData>
queryClient.prefetchQuery(options: QueryOptions): Promise<void>
queryClient.prefetchInfiniteQuery(options: InfiniteQueryOptions): Promise<void>
queryClient.fetchQuery(options: QueryOptions): Promise<TData>
queryClient.fetchInfiniteQuery(options: InfiniteQueryOptions): Promise<InfiniteData<TData>>
queryClient.isFetching(filters?: QueryFilters): number
queryClient.isMutating(filters?: MutationFilters): number
queryClient.getMutationDefaults(mutationKey: MutationKey): MutationOptions | undefined
queryClient.setMutationDefaults(mutationKey: MutationKey, options: MutationOptions): void
queryClient.getDefaultOptions(): DefaultOptions
queryClient.setDefaultOptions(options: DefaultOptions): void
queryClient.clear(): void

// SSR / Hydration (modern/HydrationBoundary.d.ts)
<QueryClientProvider client={queryClient}><HydrationBoundary state={dehydratedState}>{children}</HydrationBoundary></QueryClientProvider>

// Devtools (separate package)
import { ReactQueryDevtools } from "@tanstack/react-query-devtools"
<ReactQueryDevtools initialIsOpen={false} />
```
