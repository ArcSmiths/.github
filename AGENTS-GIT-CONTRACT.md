# ArcSmiths Git & Delivery Contract (Humans + AI Agents)

Every human developer and AI agent working in any `ArcSmiths` repository MUST follow these non-negotiable rules:

1. **No Dirty Deploys, Ever.** Never deploy to Cloudflare Pages, OCI, or Supabase from a dirty working tree or an unmerged branch. Production deploys MUST come from a clean commit on `master` (or `main`).
2. **Finish What You Start.** A task is NOT complete until all genuine code, migration, config, and doc changes are:
   - Verified (typecheck, unit tests, build),
   - Committed cleanly (no `__pycache__`, `.wrangler`, `.bak`, or local scratch dumps),
   - Pushed to `origin` (directly to `master` on unprotected repos, or via a green PR on protected repos).
3. **Zero Orphan Worktrees & Zero Stale Branches.**
   - Long-lived branches are strictly `master` (or `main`) and, on `arcbay` only, `staging`.
   - Every PR branch auto-deletes on merge (`delete_branch_on_merge: true`).
   - If you create a temporary `git worktree` or scratch directory, you MUST remove it before ending your session.
4. **Single Source of Truth for Arcbay Client Sites.**
   - All Arcbay-powered client websites live under `ArcSmiths/arcbay/sites/<slug>` and are registered in `sites/registry.json`.
   - Shared storefront scripts (`picker.js`, `website-source-v1.js`, `config.js`) live in `packages/arcbay-web-sdk/` — edit them there and run `node packages/arcbay-web-sdk/src/sync-to-sites.mjs`, never copy-paste one-off edits across client sites.
5. **Run the Workspace Doctor.** Before wrapping up multi-repo work, run `arcsmiths-doctor` (`python3 ~/Develop/arcbay/scripts/arcsmiths-doctor.py`) and confirm every repo reports `CLEAN` and `0/0`.
