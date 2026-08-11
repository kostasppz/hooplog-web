# HoopLog Web

Static landing pages for HoopLog, designed for GitHub Pages and Supabase Auth email confirmation redirects.

## Pages

- `/` — HoopLog landing page
- `/email-confirmed/` — email confirmation success page

## GitHub Pages

In the repository, open **Settings → Pages** and publish the `main` branch from the repository root.

Expected URLs:

- `https://kostasppz.github.io/hooplog-web/`
- `https://kostasppz.github.io/hooplog-web/email-confirmed/`

## Supabase configuration

In **Authentication → URL Configuration**:

- Set your production Site URL as appropriate for your app/site.
- Add this Redirect URL:

```text
https://kostasppz.github.io/hooplog-web/email-confirmed/
```

When signing up, use the same address as `emailRedirectTo`.

Example:

```js
const { data, error } = await supabase.auth.signUp({
  email,
  password,
  options: {
    emailRedirectTo: 'https://kostasppz.github.io/hooplog-web/email-confirmed/'
  }
})
```

Keep the Supabase email confirmation button pointed to:

```html
<a href="{{ .ConfirmationURL }}">Confirm email address</a>
```

## Mobile app deep link

The confirmation page currently uses:

```text
hooplog://home
```

Your mobile app must register this deep-link scheme for the **Open HoopLog** button to launch the app.
