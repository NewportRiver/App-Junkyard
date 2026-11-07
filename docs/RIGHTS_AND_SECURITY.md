# Rights, Licensing, Security, and Customer Trust

> Planning notes only. Obtain qualified legal, tax, and security review before operating a marketplace.

## Ownership and IP

- Verify the provider is an authorized owner or licensee and document the precise rights being sold or sublicensed.
- Distinguish copyright assignment, exclusive license, nonexclusive source license, and ordinary redistribution rights. State what the buyer actually receives.
- Disallow app-store scraping, decompilation of proprietary apps for resale, unauthorized source dumps, and unauthorized game assets.
- Track all upstream copyright notices, license texts, third-party assets, dependencies, trademarks, patents, and attribution duties.
- Open-source resale is not inherently forbidden, but applicable copyleft, notice, source availability, and other conditions must be met; don't suggest buyers acquire exclusivity they do not.
- Some licenses permit commercial distribution of *copies* but not relicensing under different terms. Never promise incompatible restrictions.
- Prepare copyright-takedown, repeat-infringer, dispute, and seller-warranty policies with counsel.

## Security and privacy

- Every submission is untrusted until inspected. Quarantine archives; guard against zip-slip, symlink/path tricks, archive bombs, and executable install scripts.
- Run static scans, secret scans, license/dependency scans, and sandboxed build/tests.
- Flag vulnerabilities and record the relevant scan time and dependency versions. A clean scan is not a proof of safety.
- Reject or remediate malware, credential leaks, exposed PII, and unresolved critical risks before publication.
- Secure inventory and buyer files with scoped access controls and audit logging; rotate secrets when necessary.
- Never log/store raw payment card data; prefer externally hosted checkout and tokenized references.
- Verify secure artifact delivery, checksums, backup/retention, and deletion policies.

## Buyer-facing transparency

Every product page must clearly state: what is included, license/usage rights, whether source is delivered, build status and exact environment, last inspection date, known defects, security findings, support/updates policy, and refund terms. "As-is" language does not cure misleading disclosures or extinguish applicable legal obligations.

## Seller verification

Request rights evidence, supported project history and origin, exact third-party content list, license texts, and warranties. For third-party payouts, incorporate identity verification, tax and payment requirements, sanctions/fraud screening as appropriate, and jurisdiction-specific marketplace requirements.
