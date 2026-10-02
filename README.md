# qa-bug-reports-and-triage
Templates and sample bug reports for escalating Web3 and payment issues to engineering
# QA & Bug Report Triage 🐛

This repository contains structured issue templates and sample bug reports designed to streamline communication between Customer Support and Engineering teams. Clear, reproducible bug reports reduce engineering triage time and ensure critical user friction points are resolved quickly.

## 📁 Contents

### Issue Templates
Standardized markdown templates to ensure all necessary diagnostic data is captured before escalation.
- **`ui-ux-widget-bug.md`**: For visual glitches, iframe rendering errors, or responsive design failures on the fiat-to-crypto widget.
- **`api-webhook-failure.md`**: For backend syncing issues, such as a payment partner approving a charge but the order status remaining "Pending" on-chain.

### Sample Bug Reports

**Bug Report #1: On-ramp widget fails to inject provider on Brave iOS with Shield enabled**
- **Severity:** P1 (High)
- **Description:** Users attempting to connect their wallet via the Swapped.com widget on the Brave browser (iOS) experience a silent failure when Brave Shields are set to "Aggressive". The `window.ethereum` provider is not injected.
- **Steps to Reproduce (STR):**
  1. Open Brave on iOS.
  2. Set Brave Shields to "Aggressive".
  3. Navigate to the Swapped.com staging widget.
  4. Tap "Connect Wallet".
- **Expected Behavior:** Wallet connection prompt appears.
- **Actual Behavior:** Button depresses but no action occurs; console throws `Provider not found` error.

**Bug Report #2: Slippage tolerance calculation mismatch on low-liquidity L2 pairs**
- **Severity:** P2 (Medium)
- **Description:** When routing a purchase to a low-liquidity token on Arbitrum, the quoted expected output exceeds the actual on-chain output by >2%, causing the smart contract to revert the transaction due to slippage limits.
- **Steps to Reproduce:**
  1. Initiate a $500 buy order for [Low Liquidity Token] on Arbitrum.
  2. Proceed to checkout.
  3. Observe the quoted token amount vs. the liquidity pool depth on DexScreener.
