<template>
  <!-- NavBar -->
  <b-navbar toggleable="md" type="dark" variant="info">
    <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
    <b-navbar-brand b-link to="/BookList">Merry Fairy Tales</b-navbar-brand>
    <b-collapse is-nav id="nav_collapse">
      <b-navbar-nav>
        <b-nav-item b-link to="/BookList">Grome</b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <!-- <b-nav-form>
                                            <b-form-input size="sm" class="mr-sm-2" type="text" placeholder="Search Books"/>
                                            <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
                                        </b-nav-form> -->

        <b-nav-item-dropdown right>
          <!-- Using button-content slot -->
          <template slot="button-content">
            <em>User</em>
          </template>
          <!-- <b-dropdown-item href="#">Profile</b-dropdown-item> -->
          <b-dropdown-item @click="signOut" href="/">Signout</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
  <!-- End NavBar -->
</template>

<script>
export default {
  name: "NavBar",
  data() {
    info: null
  },

  methods: {
    signOut: function() {
      var auth2 = gapi.auth2.getAuthInstance();
      auth2.signOut().then(function() {
        console.log("User signed out.");
        this.$router.push({ name: "LoginPage", query: { redirect: "/" } });
      });
    }
  },
  
};
</script>
