---
title: 'Profile'
layout: 'base.njk'
templateEngineOverride: njk,md
---

<!-- 0. HTML -->
<h3>Welcome 👇🏼</h3><h3 id="email"></h3>
<h3>Public Address 👇🏼</h3><h3 id="publicAddress"></h3>

<!-- 1. Ensure the user’s info is displayed -->
<script>
  // check that the user is logged in
  async function checkLogin() {
    const isLoggedIn = await magic.user.isLoggedIn();
    console.log({ isLoggedIn })
    if (!isLoggedIn) {
      window.location.href = '/login';
    }

    // get the user's email
    const { email, publicAddress} = await magic.user.getMetadata();

    document.querySelector('#email').innerText = email;
    document.querySelector('#publicAddress').innerText = publicAddress;
  }

  checkLogin();
</script>
