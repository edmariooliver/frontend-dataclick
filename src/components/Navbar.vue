<template>
  <nav class="nav-extended blue-grey" v-if="logado == 'true'">
    <div class="nav-wrapper">
      <a href="#" class="brand-logo center">Data Click</a>
      <a href="#" data-target="mobile-demo" class="sidenav-trigger"
        ><i class="material-icons">menu</i></a
      >
      <ul id="nav-mobile" class="hide-on-med-and-down">
        <li class="white-text"><router-link :to="'/'">Início</router-link></li>
        <li class="white-text">
          <router-link :to="'/usuarios'">Usuários</router-link>
        </li>
        <li class="white-text">
          <router-link :to="'/clubes'">Clubes</router-link>
        </li>
        <li class="white-text">
          <router-link :to="'/assinatura'">Assinatura</router-link>
        </li>
      </ul>
      <ul id="nav-mobile" class="right hide-on-med-and-down">
        <li class="white-text" style="margin-right: 10px; cursor: pointer" @click="sair">
          <strong >Sair</strong>
        </li>
      </ul>
    </div>
  </nav>

  <ul class="sidenav blue-grey" id="mobile-demo">
    <router-link :to="'/'"
      ><li class="white-text container">Início</li></router-link>
    <router-link :to="'/usuarios'"><li class="white-text container">Usuários</li></router-link>
    <router-link :to="'/clubes'"><li class="white-text container">Clubes</li></router-link>
    <router-link :to="'/assinatura'"><li class="white-text container">Assinatura</li></router-link>
    <li class="white-text container" @click="sair"><strong> Sair </strong></li>
  </ul>
</template>
<script>
export default {
  name: "Navbar",
  data() {
    return {
      logado: localStorage.getItem('isLogged')
    }
  },
  methods: {
    async sair() {
      this.api.post("api/logout", {}).then((response) => {});
      localStorage.removeItem("token");
      localStorage.removeItem("isLogged");
      window.location.href = "/login";
    },
  },
};
</script>
