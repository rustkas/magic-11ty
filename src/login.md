---
title: 'Login'
layout: 'base.njk'
templateEngineOverride: "njk.md"
---

```
<!-- 0. HTML -->
<form id="form">
    <label for="input">Email address</label>
    <input id="input" type="email" />
    <button type="submit">Login</button>
</form>
<div id="result">

<!-- 1. Use loginWithMagicLink to authenticate user -->
<script>
    const form = document.querySelector('#form');
    const input = document.querySelector('#input');
    const result = document.querySelector('#result');

    async function handleLogin(event) {
        event.preventDefault();
        
        const email = input.value;

        // token w/15-minute expiration by default
        // can extend in Magic dashboard
        const token = await magic.auth.loginWithMagicLink({
            email
        });

        result.textContent = token;

        if (token) {
            window.location.href = '/profile';
        }
    }

    form.addEventListener('submit', handleLogin);
</script>
```
