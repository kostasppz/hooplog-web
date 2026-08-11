# HoopLog Web

Static HoopLog pages for GitHub Pages and Supabase Auth flows.

## Pages

- `/` — HoopLog landing page
- `/email-confirmed/` — email confirmation success page
- `/reset-password/` — secure Supabase password reset page

## GitHub Pages

The repository publishes the `main` branch from the repository root.

URLs:

- `https://kostasppz.github.io/hooplog-web/`
- `https://kostasppz.github.io/hooplog-web/email-confirmed/`
- `https://kostasppz.github.io/hooplog-web/reset-password/`

## Email confirmation

The email confirmation page is available at:

```text
https://kostasppz.github.io/hooplog-web/email-confirmed/
```

If you use this as a Supabase redirect target, add it under **Authentication → URL Configuration → Redirect URLs**.

## Password reset

The reset page verifies the Supabase recovery `TokenHash` in the browser and then calls `supabase.auth.updateUser({ password })` to save the new password.

The recommended Supabase **Reset password** email link is:

```html
<a href="https://kostasppz.github.io/hooplog-web/reset-password/?token_hash={{ .TokenHash }}&amp;type=recovery">
  Reset password
</a>
```

A complete branded email template is included at:

```text
supabase/reset-password-email.html
```

This TokenHash-based flow is useful for mobile apps because the web page verifies the recovery token itself and does not depend on a PKCE verifier stored on the device that requested the reset.

The reset page uses only the Supabase project URL and the client-safe Supabase publishable key. No secret/service-role key is stored in this repository.

## Mobile app deep link

The completion pages currently use:

```text
hooplog://home
```

Your mobile app must register this deep-link scheme for the **Open HoopLog** button to launch the app.
