# Security Policy

## Secrets

Never commit real API keys. Create `backend/.env` locally from `backend/.env.example` and keep it private.

If a key is accidentally exposed, revoke it immediately in the provider console and create a replacement key.

## Generated Websites

Review generated HTML, CSS, and JavaScript before deploying a generated website publicly. The builder validates generated filenames and restricts output to static website file types, but generated content should still be inspected.
