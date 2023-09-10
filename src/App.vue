<template>
  <header>
    <router-link to="/">
      <h1>View<span>Movie</span></h1>
    </router-link>
  </header>
  <main>
    <router-view/> 
  </main>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-shadow: border-box;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;

  &::selection {
    background: transparent(#000, 0.5);
  }
}

body {
  width: 100%;
  height: 100vh;
  background-image: linear-gradient(to right, rgba(30, 75, 115, 1), rgba(255, 255, 255, 0));
}

#app {
  width: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  position: relative;
  height: auto;
  min-height: 100% !important;
}

a {
  text-decoration: none;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #2C3D4E;
  box-shadow: 0px 0px 6px rgba($color: #000000, $alpha: 1.0);
}

h1 {
  color: #FFF;
  font-size: 26px;

  span {
    color: aqua;
    margin-left: 5px;
  }
}
</style>
