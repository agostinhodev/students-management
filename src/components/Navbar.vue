<template>
  <div>
  <b-navbar type="dark" variant="dark">
    <b-navbar-nav>
      
      <img class="img-time-matters" :src="require(`../assets/images/logo.png`)" width="70">

      <b-nav-item-dropdown text="Student" right>

        <b-dropdown-item href="/new">New</b-dropdown-item>
        <b-dropdown-item href="/students">List</b-dropdown-item>

      </b-nav-item-dropdown>

    
    </b-navbar-nav>
  </b-navbar>
</div>
</template>
<script>

export default {
  name: "Navbar",
};
</script>
<style></style>