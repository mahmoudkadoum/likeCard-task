<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="container nav-container">
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg"/>
      <div class="wrapper">
        <nav>
          <div class="nav-links">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/">Our Products</RouterLink>
        <div class="dropdown">
          <button class="dropbtn">Resources</button>
          <div class="dropdown-content">
            <a href="#">Resource1</a>
            <a href="#">Resource2</a>
            <a href="#">Resource3</a>
          </div>
        </div>
        <RouterLink to="/">Contacts</RouterLink>
          </div>
          <div class="nav-btns">
        <button id="singnUp">Singn Up</button>
        <button id="logIn">Log In</button>
          </div>
        </nav>
      </div>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
.nav-container {
  display: flex;
}
header {
  line-height: 1.5;
  width: 100%;
  padding-block: 1.25rem;
  background-color: var(--color-neutral-100, #F8F9FB);
  border-bottom: 1px solid var(--color-neutral-600, #EAEBF0);
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  display: flex;
  justify-content: space-between;
  width: 100%;
  font-size: 12px;
  text-align: center;
}

nav .nav-links , nav .nav-btns {
  display: flex;
  align-items: center;
}
nav .nav-links {
  gap: 2rem;
}
nav .nav-btns {
  gap: 1.5rem;
}
nav .nav-btns button{
  border: none;
  outline: none;
  font-size: 15px;
  font-weight: 600;
  border-radius: 6px;
  transition: all .25s;
  cursor: pointer;
}
nav .nav-btns button:hover{
  filter: brightness(.95);
  transform: scale(1.05);
}
nav .nav-btns #singnUp{
  color: var(--color-primary);
  background: transparent;
}
nav .nav-btns #logIn{
  padding-inline: 1.125rem;
  padding-block: 0.75rem;
  color: #FFFFFF;
  background: var(--color-primary);
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  text-align: center;
  line-height: 22px;
  font-size: 15px;
  font-weight: 600;
  color: var(--color-gray-200);
}

nav a:first-of-type {
  border: 0;
}


  /* Dropdown Button */
.dropbtn {
  background-color: transparent;
  color: var(--color-gray-200);
  font-weight: 600;
  font-size: 15px;
  border: none;
  outline: none;
  position: relative;
}
.dropbtn::after {
  content: '';
  background-image: url('./assets/arrow-down.svg');
  position: absolute;
  right: -25%;
  top: 25%;
  background-size: 20px 20px;
  height: 20px;
  width: 20px;
  transform: translate(-25%,-25%);
}

.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.dropdown-content a:hover {background-color: #ddd;}

.dropdown:hover .dropdown-content {display: block;}


@media (min-width: 1024px) {
  header {
    display: flex;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    flex-grow: 1;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    font-size: 1rem;
    padding: 1rem 0;
  }

}

</style>
