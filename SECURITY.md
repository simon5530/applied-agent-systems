# Security and publication rules

## Never commit

- API keys, tokens, passwords, cookies, private keys, or .env files;
- real channel IDs, calendar records, messages, contact names, or personal preferences;
- home-directory paths, hostnames, private IPs, device identifiers, or raw logs;
- complete agent configuration, memory files, user profiles, or screenshots with notifications.

## Documentation rules

- use synthetic identities and data;
- describe roles instead of real people;
- link to public project evidence rather than copying private operational logs;
- record behavior and status codes, not credentials or private endpoints;
- separate verified, planned, and unknown claims.

## Publication gate

Follow the reusable [publication security gate](docs/PUBLICATION_SECURITY_GATE.md)
and record the result with the
[publication-audit template](templates/PUBLICATION_AUDIT.md). In summary:

1. scan current files and complete Git history with a maintained secret scanner;
2. run a separate semantic privacy review;
3. verify commit metadata uses a GitHub noreply address;
4. validate internal/external links;
5. check licenses and bundled assets;
6. confirm anonymous access only after explicit public-release approval.
