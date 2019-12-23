<template>
  <div>
  <div id="slogan" class="text-center">
  <h1>NameGator <i class="fa fa-check" aria-hidden="true"></i></h1>
  <br />
  <h6 class="text-secondary">Gerador de nomes utilizando Vue.js GraphQl e Node</h6>
  </div>
  <div id="main">
    <DomainsList></DomainsList>
</div>
</div>
</template>

<script>
    import "bootstrap/dist/css/bootstrap.css";
    import "font-awesome/css/font-awesome.css";
    import DomainsList from "./components/DomainsList"
    export default {
        name: "app",
        components: {
            DomainsList
        }
    };
</script>

<style>
    #slogan {
        margin: 30px 0px
    }
    
    #main {
        background-color: #f1f1f1;
        padding: 30px 0px;
    }
</style>