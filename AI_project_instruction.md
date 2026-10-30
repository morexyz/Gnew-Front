# Gnew Frontend — AI Project Instructions

## Purpose and project boundaries
- This frontend is an independent Gnew application (Ethereum Mainnet, PAXG/XAUt); it is NOT EchoDollar (Polygon, USDC.e/USDT).
- It is distinct from the public Gnew landing page (`morexyz/Gnew`) and the operator bot (`morexyz/Gnew-Bot`). Do not update either repository without explicit authorization.
- Do not publish proprietary contract strategy details on the public landing page.

## Source, architecture and constraints
- Based on `source/frontend/approve-run.html` in the supplied EchoDollar handoff archive.
- Native, dependency-free HTML/CSS/JavaScript with injected EIP-1193 wallet interface, no bundler.
- Preserve source structure and methods unless necessary for Ethereum compatibility or preventing unsafe transactions.
- Gnew contract is NOT yet deployed; `setup.html` has no default contract address and is not production-ready.

## Step 1 — Setup page adapted (pending user validation)
- Replaced Polygon and USDC.e/USDT user-facing values with Ethereum Mainnet and PAXG (18 decimals)/XAUt (6 decimals).
- Removed default EchoDollar contract address; contract must be provided after deployment.
- Changed default approve amounts to zero and MAX approvals to unchecked.
- Enforced Ethereum Mainnet check before sending any transaction.
- Before approve, revoke or operator-only run, requires an actual deployed contract at the address whose token1, token2 and pool match Gnew's Ethereum configuration.
- Retained existing contract API selectors and wallet interaction design. No trading strategy changes.
- `setup.html` contains operator-only `run(user)` for operators only; normal customers should not use it.

## Upcoming separately approved milestone
- Adapt `dashboard.html` next. Do NOT copy the old USDC+USDT value chart as if it were a USD value for PAXG+XAUt.
- Use Etherscan links and ETH gas labels; adapt history RPC behavior and 18/6 decimal formatting.
- After Gnew contract deployment: set verified contract address and deployment block; test both directions and approvals on Ethereum before production publication.

## Testing
- Syntax: `node --check` against the embedded `<script>` content (as extracted separately).
- Browser/wallet transaction tests have not yet been performed. No transactions are authorized by merely creating this artifact.
- Keep all work minimal, review diffs, never use `git add .`.