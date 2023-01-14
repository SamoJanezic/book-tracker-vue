<template>
    <nav class="flex-container">
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

.flex-container {
  display: flex;
  flex-direction: row;
  /* background-color: rgb(205, 233, 242); */
  align-items: flex-end;
  padding-bottom: 12px;
  background-color: rgb(0, 0, 0);
}

.link-btn {
  padding: 5px 20px;
  margin: 0px 18px;
  background-color: rgba(255, 240, 240, 0.633);
  border: 2px solid black;
  border-radius: 0px 0px;
  transition: 350ms ease-in-out;
}

.link-btn:hover {
  /* border-radius: 20px 0px; */
  color: blue;
  background-color: lightblue;
}

</style>