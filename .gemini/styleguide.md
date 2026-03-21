# UCP JavaScript/TypeScript SDK (nan-js-sdk) Style Guide

<!--*
freshness: { owner: 'chadliu' reviewed: '2026-03-21' }
*-->

This guide defines the standards for the `@ucp-js/sdk`, focusing on type-safe, asynchronous, and agnostic commerce integration.

## Core Principles

### 1. Brand Neutrality
*   **DO NOT** use brand names (e.g., Target, Shopify) in code, comments, or documentation.
*   **DO** use role-based terms: `Merchant`, `Provider`, `Agent`, `Buyer`.

### 2. Type Safety
*   **TypeScript:** Use strict typing. Avoid `any` unless absolutely necessary (e.g., for low-level parsing of unknown inputs).
*   **Zod:** Use `zod` for runtime validation of incoming UCP payloads. Every API response should be validated against a schema.
*   **Interfaces over Types:** Prefer `interface` for defining object structures that might be extended.

### 3. Asynchronous Patterns
*   **Async/Await:** Prefer `async/await` over raw `Promise.then()` chains for better readability.
*   **Error Handling:** Always wrap async calls in `try/catch` or handle `.catch()` to prevent unhandled rejections.

## Technical Standards

### TypeScript Code Style
*   **Formatting:** Enforced via Prettier. Follow the repository's `.prettierrc` (2-space indentation).
*   **Imports:** Use `import type` for type-only imports to optimize build bundles.
*   **Naming:** `camelCase` for variables/functions, `PascalCase` for classes/interfaces, `UPPER_SNAKE_CASE` for constants.

### Repository Specifics
*   **Build Output:** Do not commit files in the `dist/` directory.
*   **Documentation:** Every public class and method should have a JSDoc comment.
    ```typescript
    /**
     * Resolves a UCP mandate for a given checkout.
     * @param checkoutId - The unique identifier for the checkout.
     * @returns A promise resolving to the mandate details.
     */
    async resolveMandate(checkoutId: string): Promise<Mandate> { ... }
    ```

## Semantic Review Focus
Gemini should prioritize:
1.  **Zod Schema Alignment:** Do the Zod schemas match the official UCP specifications?
2.  **Agnosticism:** Ensure no partner-specific logic is embedded in the SDK core.
3.  **Modern JS:** Check for usage of modern ESNext features where appropriate.
