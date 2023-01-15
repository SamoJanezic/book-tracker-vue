<template>
    <nav class="flex-container main">
      <router-link class="link-btn" to="/">Home</router-link>
      <router-link class="link-btn" to="/book-list">Book List</router-link>
      <router-link class="link-btn" to="/add-book">Add Book</router-link>
    </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #000000;
}

/* .flex-container {
  display: flex;
  flex-direction: row;
  align-items: flex-end;
  padding-bottom: 12px;
} */

.link-btn {
  padding: 5px 20px;
  margin: 0px 18px;
  background-color: rgba(255, 240, 240, 0.633);
  border: 2px solid rgb(146, 141, 141);
  border-radius: 10px 10px;
  transition: 350ms ease-in-out;
  color: rgb(146, 141, 141);
}

.link-btn:hover {
  /* border-radius: 20px 0px; */
  color: blue;
  background-color: lightblue;
}

nav.main {
  height: 20px;
  /* position: fixed; */
  box-shadow: 0px 0px 20px rgb(200, 219, 189) inset;
  transition: .10s linear all;
  padding: 30px 0px 20px 0px;
  /* width: 100vw; */
  
}

nav:hover {
  box-shadow: 0px 0px 70px rgb(200, 219, 189) inset;
}
</style>