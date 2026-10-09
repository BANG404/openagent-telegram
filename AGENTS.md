# Plugin maintenance

Source adaptation is in src/, immutable upstream identity is in provenance.json. Use Bun. Copy build.bun.lock to bun.lock and run bun install --frozen-lockfile --ignore-scripts before bun run build. Review upstream access controls before changing channel behavior. After rebuilding, update artifact SHA-256 values in provenance.json, run bun test tests and production Runtime acceptance. Bump plugin.json and package.json versions before publishing new bytes. Never commit credentials or modify user OpenAgent state.
