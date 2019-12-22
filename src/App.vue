<template>
  <div>
  <div id="slogan" class="text-center">
  <h1>NameGator <i class="fa fa-check" aria-hidden="true"></i></h1>
  <br />
  <h6 class="text-secondary">Gerador de nomes utilizando Vue.js GraphQl e Node</h6>
  </div>
  <div id="main">
    <div class="container">
      <div class="row">
        <div class="col-md">
          <h5>Prefixos <span class="badge badge-info">{{ prefixes.length }}</span></h5>
          <div class="card">
             <div class="card-body">
              <ul class="list-group">
                <li class="list-group-item" v-for="prefix in prefixes" v-bind:key="prefix">
                  <div class="row">
                    <div class="col-md">
                      {{ prefix }}
                    </div>
                    <div class="col-md text-right">
                      <button type="button" class="btn btn-info" v-on:click="removePrefix(prefix)"><i class="fa fa-trash" aria-hidden="true"></i> </button>
                    </div>
                  </div>
                </li>
              </ul>
              <br/>
              <div class="input-group">
                <input type="text" class="form-control" v-model="prefix"  v-on:keyup.enter="addPrefix(prefix)" placeholder="Digite o Prefixo" />
                <div class="input-group-append">
                  <button type="button" class="btn btn-info" v-on:click="addPrefix(prefix)"> <i class="fa fa-plus" aria-hidden="true"></i> </button>
                </div>
              </div>
            </div>
        </div>
      </div>
        <div class="col-md">
          <h5>Sufixos  <span class="badge badge-info">{{ sufixes.length }}</span></h5>
          <div class="card">
            <div class="card-body">
              <ul class="list-group">
                <li class="list-group-item" v-for="sufix in sufixes" v-bind:key="sufix">
                  <div class="row">
                    <div class="col-md">
                      {{ sufix }}
                    </div>
                    <div class="col-md text-right">
                      <button type="button" class="btn btn-info" v-on:click="removeSufix(sufix)"><i class="fa fa-trash" aria-hidden="true"></i> </button>
                    </div>
                  </div>
                </li>
              </ul>
              <br/>
              <div class="input-group">
                <input type="text" class="form-control" v-model="sufix" v-on:keyup.enter="addSufix(sufix)" placeholder="Digite o Sufixo" />
                <div class="input-group-append">
                  <button type="button" class="btn btn-info"  v-on:click="addSufix(sufix)"> <i class="fa fa-plus" aria-hidden="true"></i> </button>
                </div>
              </div>
          </div>
        </div>
      </div>
    </div>
    <br/>
    <h5>Dominios  <span class="badge badge-info">{{ domains.length }}</span></h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="domain in domains" v-bind:key="domain">
              {{ domain }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</div>
</div>
</template>

<script>
    import "bootstrap/dist/css/bootstrap.css";
    import "font-awesome/css/font-awesome.css";
    export default {
        name: "app",
        data: function() {
            return {
                prefix: "",
                sufix: "",
                prefixes: ["Air", "Jet", "Flight"],
                sufixes: ["Hub", "Station", "Mart"],
                domains: ["AirHub", "AirStation", "AirMart", "JetHub", "JetSation", "JetMart", "FligthHub", "FligthStation", "FligthMart"]
            };
        },
        methods: {
            addPrefix(prefix) {
                this.prefixes.push(prefix);
                this.prefix = "";
                this.generate();
            },
            addSufix(sufix) {
                this.sufixes.push(sufix);
                this.sufix = "";
                this.generate();
            },
            removeSufix(sufix) {
                this.sufixes.shift(sufix);
                this.generate();
            },
            removePrefix(sufix) {
                this.prefixes.shift(sufix);
                this.generate();
            },
            generate() {
                this.domains = [];
                for (const prefix of this.prefixes) {
                    for (const sufix of this.sufixes) {
                        this.domains.push(prefix + sufix);
                    }
                }
            }
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