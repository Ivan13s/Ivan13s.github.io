<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/submit">Submit an Issue</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<style>
nav {
  margin-bottom: 20px;
}
nav a {
  margin-right: 15px;
}
</style>

