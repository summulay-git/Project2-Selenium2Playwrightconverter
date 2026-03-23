# SOP: Selenium to Playwright (JS/TS) Conversion

## Overview
This SOP defines the deterministic rules and LLM guidance for converting Selenium Java (TestNG) tests to Playwright.

## 1. Imports and Setup
- Remove: `import org.openqa.selenium.*`, `import org.testng.annotations.*`.
- Add: `const { test, expect } = require('@playwright/test');` (JS) or `import { test, expect } from '@playwright/test';` (TS).

## 2. Test Structure
- Map `@Test` methods to `test('description', async ({ page }) => { ... });`.
- Map `@BeforeMethod` to `test.beforeEach(async ({ page }) => { ... });`.
- Map `@AfterMethod` to `test.afterEach(async ({ page }) => { ... });`.

## 3. Method Mapping
| Selenium (Java) | Playwright (JS/TS) |
| --- | --- |
| `driver.get(url)` | `await page.goto(url)` |
| `driver.findElement(By.id("id"))` | `page.locator('#id')` |
| `driver.findElement(By.name("n"))` | `page.locator('[name="n"]')` |
| `element.sendKeys("val")` | `await element.fill("val")` |
| `element.click()` | `await element.click()` |
| `new WebDriverWait(...)` | (Remove, rely on auto-waiting) |

## 4. Assertions
- `Assert.assertEquals(actual, expected)` -> `expect(actual).toBe(expected)`.
- `Assert.assertTrue(condition)` -> `expect(condition).toBeTruthy()`.

## 5. Implementation Rules
- Always use `await` for Playwright actions.
- Use `page.getByRole` or `page.getByText` where possible for better resilience.
- Maintain variable names from the original code where logical.
