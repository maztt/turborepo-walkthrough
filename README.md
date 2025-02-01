# turborepo-walkthrough

Repository for the Turborepo exploration

## Analogy on the structure

- City: `root repository`, in this case a monorepo;
- Neighbourhoods: `apps` and `packages`, each one have their own unique characteristics and purpose;
- Zoning/Areas: `workspaces`, it defines which/where are the neighbourhoods, and which areas are designated for specific types of buildings (packages);
- City hall: `root package.json`, it defines the overall rules/configurations for the entire city;
- Neighbourhood guidelines: `nested package.json`, it defines what resources that neighbourhood needs and what activities (scripts) can take place. (e.g. a neighbourhood focused on residential living might have different needs and behaviors to a commercial neighbourhood);
- City's infrastructure plan: `turbo.json` , it defines how different neighbourhoods connect and interact with each other, responsible for the **build pipelines** (like roads and public transport ease the movement between hoods, it specifies how to build and deploy each app/package efficiently), and **caching strategies** (traffic management systems that optimize flow and reduce congestions);

## Usage tips

> To quickly install dependencies in multiple packages:

```
pnpm install jest --save-dev --recursive --filter=web --filter=@repo/ui --filter=@repo/web
```

> To bump all versions in every package

```
npm install typescript@latest --workspaces
```


## Best practices

- Keep your `root package.json` as clean as possible, making sense to keep only a few like turbo, husky or lint-staged. Other dependencies should belong in their own `nested package.json`.
- The `name` in each of the `nested package.json` should follow a `@{orgName}/{packageName}` pattern to avoid conflict.
- It is recommended to create packages that have a "single purpose" (e.g. `@repo/ui` for all your shared UI components or `@repo/tool-specific-config`).
