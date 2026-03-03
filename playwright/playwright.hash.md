---
Language: Playwright
Version: 1.x
Fidelity: 100% (Physical Disk Reference)
State_ID: BigInt(0x1)
LSP_Discovery_Root: "@root/node_modules/playwright/package.json"
Grammar_Lock: "@root/hashes/grammar/playwright.hash.md"
---

/** [Project].Grammar.Playwright - Linguistic DNA anchor for Playwright 1.x */

## [SDK_Discovery_Map]
/** === playwright (4 definition files) === */
/** @Ref: @root/node_modules/playwright/index.d.ts */
/** @Ref: @root/node_modules/playwright/test.d.ts */
/** @Ref: @root/node_modules/playwright/types/test.d.ts */
/** @Ref: @root/node_modules/playwright/types/testReporter.d.ts */
/** === playwright-core (4 definition files) === */
/** @Ref: @root/node_modules/playwright-core/index.d.ts */
/** @Ref: @root/node_modules/playwright-core/types/types.d.ts */
/** @Ref: @root/node_modules/playwright-core/types/structs.d.ts */
/** @Ref: @root/node_modules/playwright-core/types/protocol.d.ts */

## [SDK_Imports / Namespaces]
```ts
// Test framework
import { test, expect } from "@playwright/test"
import type { Page, Locator, BrowserContext, Browser, Frame, ElementHandle, Request, Response, Route, Worker, Download, Dialog, ConsoleMessage, FileChooser, Selectors, BrowserType, LaunchOptions, ViewportSize, Cookie, StorageState, TestInfo, TestType, PlaywrightTestConfig, PlaywrightTestOptions, PlaywrightWorkerOptions, PlaywrightWorkerFixtures, PlaywrightTestFixtures, FullConfig, FullProject, FullResult, Reporter, TestCase, TestResult, TestStep, TestError, Suite } from "@playwright/test"

// Library API (non-test usage)
import { chromium, firefox, webkit, devices } from "playwright"
import type { BrowserServer, CDPSession, Tracing, APIRequestContext, APIResponse } from "playwright"
```

## [Core_Primitives]
```ts
// Test definition (types/test.d.ts)
test(title: string, body: (args: PlaywrightTestFixtures) => Promise<void>): void
test.describe(title: string, body: () => void): void
test.describe.serial(title: string, body: () => void): void
test.describe.parallel(title: string, body: () => void): void
test.describe.configure({ mode: "serial" | "parallel", retries?, timeout? }): void
test.beforeAll(body: (args) => Promise<void>): void
test.beforeEach(body: (args) => Promise<void>): void
test.afterAll(body: (args) => Promise<void>): void
test.afterEach(body: (args) => Promise<void>): void
test.skip(condition?: boolean, description?: string): void
test.fixme(condition?: boolean, description?: string): void
test.slow(condition?: boolean, description?: string): void
test.only(title: string, body: (args) => Promise<void>): void
test.fail(condition?: boolean, description?: string): void
test.use(options: PlaywrightTestOptions): void
test.step<T>(title: string, body: () => Promise<T>): Promise<T>
test.extend<T, W>(fixtures: Fixtures<T, W>): TestType<T, W>
test.info(): TestInfo

// Default fixtures (built-in via test.d.ts)
// { page, context, browser, browserName, request }
test("example", async ({ page, context, browser, browserName, request }) => {})

// Page (playwright-core/types/types.d.ts — the primary interface)
interface Page {
  // Navigation
  goto(url: string, options?: { timeout?, waitUntil?: "load" | "domcontentloaded" | "networkidle" | "commit" }): Promise<Response | null>
  goBack(options?): Promise<Response | null>
  goForward(options?): Promise<Response | null>
  reload(options?): Promise<Response | null>
  url(): string
  title(): Promise<string>
  content(): Promise<string>
  setContent(html: string, options?): Promise<void>

  // Locators (preferred API — types/types.d.ts)
  locator(selector: string, options?: { has?, hasNot?, hasText?, hasNotText? }): Locator
  getByRole(role: AriaRole, options?: { name?, exact?, checked?, disabled?, expanded?, includeHidden?, level?, pressed?, selected? }): Locator
  getByText(text: string | RegExp, options?: { exact? }): Locator
  getByLabel(text: string | RegExp, options?: { exact? }): Locator
  getByPlaceholder(text: string | RegExp, options?: { exact? }): Locator
  getByAltText(text: string | RegExp, options?: { exact? }): Locator
  getByTitle(text: string | RegExp, options?: { exact? }): Locator
  getByTestId(testId: string | RegExp): Locator

  // Actions (on page level)
  click(selector: string, options?): Promise<void>
  fill(selector: string, value: string, options?): Promise<void>
  type(selector: string, text: string, options?): Promise<void>
  press(selector: string, key: string, options?): Promise<void>
  check(selector: string, options?): Promise<void>
  uncheck(selector: string, options?): Promise<void>
  selectOption(selector: string, values, options?): Promise<string[]>
  setInputFiles(selector: string, files, options?): Promise<void>
  hover(selector: string, options?): Promise<void>
  dragAndDrop(source: string, target: string, options?): Promise<void>

  // Wait
  waitForSelector(selector: string, options?: { state?: "attached" | "detached" | "visible" | "hidden", timeout? }): Promise<ElementHandle | null>
  waitForLoadState(state?: "load" | "domcontentloaded" | "networkidle", options?): Promise<void>
  waitForURL(url: string | RegExp | ((url: URL) => boolean), options?): Promise<void>
  waitForTimeout(timeout: number): Promise<void>
  waitForEvent(event: string, optionsOrPredicate?): Promise<any>
  waitForResponse(urlOrPredicate, options?): Promise<Response>
  waitForRequest(urlOrPredicate, options?): Promise<Request>
  waitForFunction(pageFunction, arg?, options?): Promise<JSHandle>

  // Evaluation
  evaluate<R>(pageFunction: () => R): Promise<R>
  evaluateHandle(pageFunction, arg?): Promise<JSHandle>
  addScriptTag(options: { url? | content? | path? }): Promise<ElementHandle>
  addStyleTag(options: { url? | content? | path? }): Promise<ElementHandle>
  exposeFunction(name: string, callback: Function): Promise<void>
  exposeBinding(name: string, callback: Function, options?): Promise<void>

  // Screenshots & Video
  screenshot(options?: { path?, fullPage?, clip?, type?: "png" | "jpeg", quality?, omitBackground?, mask?, animations? }): Promise<Buffer>
  video(): Video | null

  // Network
  route(url: string | RegExp | ((url: URL) => boolean), handler: (route: Route, request: Request) => Promise<void>): Promise<void>
  unroute(url, handler?): Promise<void>
  setExtraHTTPHeaders(headers: Record<string, string>): Promise<void>

  // Events
  on(event: "close" | "console" | "crash" | "dialog" | "download" | "filechooser" | "frameattached" | "framedetached" | "framenavigated" | "load" | "pageerror" | "popup" | "request" | "requestfailed" | "requestfinished" | "response" | "websocket" | "worker", handler): void

  // State
  close(options?): Promise<void>
  isClosed(): boolean
  viewportSize(): { width: number; height: number } | null
  setViewportSize(viewportSize: { width: number; height: number }): Promise<void>
  frames(): Frame[]
  mainFrame(): Frame
  keyboard: Keyboard
  mouse: Mouse
  touchscreen: Touchscreen
}

// Locator (types/types.d.ts — preferred over selectors)
interface Locator {
  // Actions
  click(options?): Promise<void>
  dblclick(options?): Promise<void>
  fill(value: string, options?): Promise<void>
  clear(options?): Promise<void>
  type(text: string, options?): Promise<void>
  press(key: string, options?): Promise<void>
  pressSequentially(text: string, options?): Promise<void>
  check(options?): Promise<void>
  uncheck(options?): Promise<void>
  setChecked(checked: boolean, options?): Promise<void>
  selectOption(values, options?): Promise<string[]>
  setInputFiles(files, options?): Promise<void>
  hover(options?): Promise<void>
  focus(options?): Promise<void>
  blur(options?): Promise<void>
  tap(options?): Promise<void>
  dragTo(target: Locator, options?): Promise<void>
  scrollIntoViewIfNeeded(options?): Promise<void>

  // Assertions/Queries
  textContent(options?): Promise<string | null>
  innerText(options?): Promise<string>
  innerHTML(options?): Promise<string>
  inputValue(options?): Promise<string>
  getAttribute(name: string, options?): Promise<string | null>
  isChecked(options?): Promise<boolean>
  isDisabled(options?): Promise<boolean>
  isEditable(options?): Promise<boolean>
  isEnabled(options?): Promise<boolean>
  isHidden(options?): Promise<boolean>
  isVisible(options?): Promise<boolean>
  count(): Promise<number>
  allInnerTexts(): Promise<string[]>
  allTextContents(): Promise<string[]>
  all(): Promise<Locator[]>
  boundingBox(options?): Promise<{ x, y, width, height } | null>

  // Filtering / Chaining
  filter(options?: { has?, hasNot?, hasText?, hasNotText? }): Locator
  nth(index: number): Locator
  first(): Locator
  last(): Locator
  and(locator: Locator): Locator
  or(locator: Locator): Locator
  locator(selector: string, options?): Locator
  getByRole(role, options?): Locator
  getByText(text, options?): Locator
  getByLabel(text, options?): Locator
  getByTestId(testId): Locator
  getByPlaceholder(text, options?): Locator
  getByAltText(text, options?): Locator
  getByTitle(text, options?): Locator

  // Screenshots
  screenshot(options?): Promise<Buffer>

  // Wait
  waitFor(options?: { state?: "attached" | "detached" | "visible" | "hidden", timeout? }): Promise<void>
}
```

## [Assertions_API]
```ts
// Web-first assertions (types/test.d.ts)
await expect(locator).toBeVisible(options?)
await expect(locator).toBeHidden(options?)
await expect(locator).toBeEnabled(options?)
await expect(locator).toBeDisabled(options?)
await expect(locator).toBeEditable(options?)
await expect(locator).toBeChecked(options?)
await expect(locator).toBeEmpty(options?)
await expect(locator).toBeFocused(options?)
await expect(locator).toBeInViewport(options?)
await expect(locator).toBeAttached(options?)
await expect(locator).toHaveText(text: string | RegExp | (string | RegExp)[], options?)
await expect(locator).toContainText(text: string | RegExp | (string | RegExp)[], options?)
await expect(locator).toHaveValue(value: string | RegExp, options?)
await expect(locator).toHaveValues(values: (string | RegExp)[], options?)
await expect(locator).toHaveAttribute(name: string, value?: string | RegExp, options?)
await expect(locator).toHaveClass(expected: string | RegExp | (string | RegExp)[], options?)
await expect(locator).toHaveCSS(name: string, value: string | RegExp, options?)
await expect(locator).toHaveId(id: string | RegExp, options?)
await expect(locator).toHaveCount(count: number, options?)
await expect(locator).toHaveScreenshot(name?, options?)
await expect(locator).toHaveAccessibleName(name: string | RegExp, options?)
await expect(locator).toHaveAccessibleDescription(description: string | RegExp, options?)
await expect(locator).toHaveRole(role: AriaRole, options?)

// Page assertions
await expect(page).toHaveURL(url: string | RegExp, options?)
await expect(page).toHaveTitle(title: string | RegExp, options?)
await expect(page).toHaveScreenshot(name?, options?)

// API response assertions
await expect(response).toBeOK()
await expect(response).not.toBeOK()

// Negation
await expect(locator).not.toBeVisible()

// Soft assertions (don't stop test on failure)
await expect.soft(locator).toBeVisible()

// Polling assertions
await expect.poll(async () => await page.evaluate(() => window.data), { timeout: 5000 }).toBe("ready")
```

## [Architectural_Laws]
- **Export_Law**: Config as `playwright.config.ts`. Page Object Models as classes in `pages/` directory. Fixtures via `test.extend<Fixtures>()`. Global setup/teardown via `globalSetup` / `globalTeardown` config.
- **Transformation_Law**: Use Locators over selectors — they're auto-retrying and strictness-enforced. Use `getByRole/getByText/getByLabel/getByTestId` over CSS/XPath. Web-first assertions auto-wait.
- **Propagation_Law**: Failed assertions include diff and screenshot. Tests auto-retry on flakiness (via `retries` config). Trace viewer for debugging failed tests. Videos and screenshots on failure.

## [Standard_Library_Signatures]
```ts
// Config (types/test.d.ts)
import { defineConfig, devices } from "@playwright/test"
export default defineConfig({
  testDir: "./tests",
  fullyParallel: true,
  forbidOnly: !!process.env.CI,
  retries: process.env.CI ? 2 : 0,
  workers: process.env.CI ? 1 : undefined,
  reporter: "html" | [["html", { outputFolder: "report" }]] | [["junit", { outputFile: "results.xml" }]],
  timeout: 30000,
  expect: { timeout: 5000, toHaveScreenshot: { maxDiffPixels?, maxDiffPixelRatio?, threshold? } },
  use: {
    baseURL: "http://localhost:3000",
    trace: "on-first-retry" | "on" | "off" | "retain-on-failure",
    screenshot: "only-on-failure" | "on" | "off",
    video: "on-first-retry" | "on" | "off" | "retain-on-failure",
    headless: true,
    viewport: { width: 1280, height: 720 },
    ignoreHTTPSErrors: true,
    actionTimeout: 0,
    navigationTimeout: 30000,
    locale: "en-US",
    timezoneId: "America/New_York",
    colorScheme: "dark" | "light" | "no-preference",
    geolocation: { latitude, longitude },
    permissions: ["geolocation"],
    extraHTTPHeaders: { "Accept-Language": "en" },
    storageState: "auth.json",
    userAgent: string,
    httpCredentials: { username, password },
    launchOptions: { slowMo?: number },
  },
  projects: [
    { name: "chromium", use: { ...devices["Desktop Chrome"] } },
    { name: "firefox", use: { ...devices["Desktop Firefox"] } },
    { name: "webkit", use: { ...devices["Desktop Safari"] } },
    { name: "mobile-chrome", use: { ...devices["Pixel 5"] } },
    { name: "mobile-safari", use: { ...devices["iPhone 12"] } },
  ],
  webServer: { command: "npm run dev", port: 3000, reuseExistingServer: !process.env.CI },
  globalSetup: "./global-setup.ts",
  globalTeardown: "./global-teardown.ts",
})

// API testing (APIRequestContext)
const { request } = await test.extend({})
const response = await request.get("/api/users")
const response = await request.post("/api/users", { data: { name: "Alice" }, headers: {} })
const response = await request.put("/api/users/1", { data })
const response = await request.delete("/api/users/1")
const json = await response.json()
expect(response.ok()).toBeTruthy()

// Browser context (types/types.d.ts)
const context = await browser.newContext({ viewport, locale, permissions, geolocation, storageState, httpCredentials })
const page = await context.newPage()
await context.addCookies([{ name, value, url }])
const cookies = await context.cookies()
await context.clearCookies()
await context.grantPermissions(["geolocation"])
await context.setGeolocation({ latitude, longitude })
await context.close()
```
