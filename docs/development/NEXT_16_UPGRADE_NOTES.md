# Next.js 16 Upgrade Notes

## Summary

This branch updates the platform UI project dependencies toward the Next.js 16 stable line.

## Updated dependencies

- `next`: `15.3.1` -> `^16.2.4`
- `react`: `19.1.0` -> `^19.2.4`
- `react-dom`: `19.1.0` -> `^19.2.4`
- `@types/react`: `^19.1.2` -> `^19.2.4`
- `@types/react-dom`: `^19.1.2` -> `^19.2.4`
- `eslint-config-next`: `15.3.1` -> `^16.2.4`

## Runtime requirement

Next.js 16 requires Node.js `>=20.9.0`, so `package.json` now declares:

```json
"engines": {
  "node": ">=20.9.0"
}
```

The GitHub Actions workflow already uses Node 20, but local development should use Node 20.9+ or Node 22+.

## Scripts

The project already uses `eslint .` instead of `next lint`, so no `next lint` migration was required.

The project does not currently use custom Turbopack or Webpack configuration in `next.config.ts`.

## Required local follow-up

Because this change was made through repository file updates rather than running `npm install` in a local clone, the lockfile still needs to be regenerated in a development environment:

```bash
npm install
npm run typecheck
npm run lint
npm run build
```

Then commit the updated `package-lock.json` in this same branch before merging.

## Review checklist

- [ ] `npm install` was run and `package-lock.json` updated.
- [ ] `npm run typecheck` passes.
- [ ] `npm run lint` passes.
- [ ] `npm run build` passes.
- [ ] No UI behavior changed beyond dependency compatibility.
- [ ] No Supabase, D4Sign, Asaas, migration, or backend logic was changed.
