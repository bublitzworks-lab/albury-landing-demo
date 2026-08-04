# Security Notes

This site is currently a static landing page. Static hosting greatly reduces attack surface, but production security still depends on deployment headers, third-party services, and any future form backend.

## Current hardening

- Vercel security headers are configured in `vercel.json`.
- Assets are cached aggressively with immutable cache headers.
- External links opened in a new tab use `rel="noopener noreferrer"`.
- Contact form inputs include length limits and client-side validation.
- A hidden honeypot field helps filter basic bot submissions.
- User input is never injected with `innerHTML`.

## Before connecting the form to a CRM or backend

- Validate and sanitize every field again on the server.
- Add rate limiting per IP and per email/phone.
- Add spam protection such as Turnstile, reCAPTCHA, or a server-side challenge.
- Store secrets only in Vercel environment variables.
- Never expose API keys in HTML or client-side JavaScript.
- Update `connect-src` and `form-action` in `vercel.json` only for the exact endpoint you use.

## Traffic resilience

- Keep large images in optimized WebP format.
- Keep assets fingerprinted or cached as immutable.
- Use Vercel production deployment instead of serving from a local file path.
- Monitor form submission errors and page performance after launch.
