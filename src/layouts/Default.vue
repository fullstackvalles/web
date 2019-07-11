<template>
  <div>
    <header class="header">
      <h1 class="header__logo">
        <g-link to="/"><g-image :alt="$static.metaData.siteName" src="~/assets/img/fsv-logo-shadow.png" width="400" quality="75"></g-image></g-link>
      </h1>
      <h2 class="header__subtitle">Un meetup de desenvolupament web que no es fa a Barcelona</h2>

      <ul class="links">
        <li class="links__item" v-for="link in links">
          <a :href="link.url" target="_blank" rel="noopener" :class="`links__logo links__logo--${link.name}`">
              <img :src="`/${link.name}-logo.svg`" :alt="link.name">
          </a>
        </li>
      </ul>
    </header>
    <main>
      <slot/>
    </main>
  </div>
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

<script>
export default {
  data() {
    return {
      links: [
        {
          url: "https://www.meetup.com/Full-Stack-Valles/",
          name: "meetup"
        },
        {
          url: "https://twitter.com/fullstackvalles",
          name: "twitter"
        },
        {
          url: "https://t.me/joinchat/CNyvY1Rb-p-SYungo5Ooag",
          name: "telegram"
        }
      ]
    };
  }
};
</script>


<style lang="scss">
$primary-color: #F6CD37;
$secondary-color: #C55812;
* {
  box-sizing: border-box;
}
.header {
  min-height: 100vh;
  padding: 2rem 1rem;
  background: url('~@/assets/img/header-bg.jpg') no-repeat center;
  background-size: cover;
  color: #fff;
  text-align: center;
  &__logo {
    text-align: center;
    img {
      max-width: 100%;
    }
  }
  &__subtitle {
    max-width: 37rem;
    margin: 0 auto 1.5em;
    line-height: 1.2;
    font-size: 2rem;
  }
}
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
  background: darken($secondary-color, 35);
}

.layout {
  max-width: 760px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}
.links {
  display: flex;
  justify-content: center;
  list-style: none;
  margin: 1rem 0;
  padding: 0;
  &__item {
      margin: 0 .5rem;
    text-align: center;
    text-transform: capitalize;
    @media screen and (min-width: 450px) {
      margin: 0 2rem;
    }
  }
  &__logo {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 5rem;
    height: 5rem;
    margin: 0 0 .5rem;
    background: $secondary-color;
    border-radius: 50%;
    color: #fff;
    img {
      width: 60%;
    }
    &--telegram img {
      margin-right: .4rem;
    }
  }
}
</style>
