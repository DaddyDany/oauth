<template>
  <div
    class="home"
    style="
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      top: -50px;
    "
  >
    <div>
      <h1>Inicio de sesión con Oauth</h1>
      <div v-if="!$auth.loading">
        <b-button
          variant="outline-primary"
          v-if="!$auth.isAuthenticated"
          @click="login"
          >Iniciar Sesión</b-button
        >
        <b-button
          variant="outline-danger"
          v-if="$auth.isAuthenticated"
          @click="logout"
          >Cerrar Sesión</b-button
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "home",
  methods: {
    login() {
      this.$auth.loginWithRedirect();
    },
    logout() {
      this.$auth.logout({
        logoutParams: {
          returnTo: window.location.origin,
        },
      });
    },
  },
};
</script>
