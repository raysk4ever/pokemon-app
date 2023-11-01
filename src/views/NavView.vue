<template>
  <nav>
    <h1>Pokemon App</h1>
    <div class="search-bar">
      <input placeholder="Search for Pokemon..."/>
    </div>
    <div>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/test">Contribute</RouterLink>
    </div>
  </nav>
</template>

<style>
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid #eee;
    padding: 10px;
    position: sticky;
    top: 0px;
    background-color: white;
    z-index: 1;
  }
  nav > div {
    display: flex;
    gap: 1rem;
  }
  nav > div a {
    padding: 10px;
  }
  .search-bar input {
    border: none;
    background-color: #eee;
    padding: 8px 16px;
    width: 300px;
    outline: 1px solid #999;
  }
</style>