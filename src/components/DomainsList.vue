<template>
  <div>
  <div id="main">
    <div class="container">
      <div class="row">
        <div class="col-md">
          <AppItemList title="Prefixos" v-bind:items="prefixes" v-on:addItem="addPrefix" v-on:removeItem="removePrefix"></AppItemList>
      </div>
        <div class="col-md">
          <AppItemList title="Sufixos" v-bind:items="sufixes"  v-on:addItem="addSufix" v-on:removeItem="removeSufix"></AppItemList>
      </div>
    </div>
    <br/>
    <h5>Dominios  <span class="badge badge-info">{{ domains.length }}</span></h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="domain in domains" v-bind:key="domain.name">
            <div class="row">
              <div class="col-md">
                {{ domain.name }}
              </div>
              <div class="col-md text-right">
                <a type="button" class="btn btn-info" v-bind:href="domain.checkout" target="_blank"> <i class="fa fa-shopping-cart" aria-hidden="true"></i> </a>
              </div>
            </div>
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
    import AppItemList from "./AppItemList"
    export default {
        name: "app",
        components: {
            AppItemList
        },
        data: function() {
            return {
                prefixes: ["Air", "Jet", "Flight"],
                sufixes: ["Hub", "Station", "Mart"],
            };
        },
        methods: {
            addPrefix(prefix) {
                this.prefixes.push(prefix);
            },
            addSufix(sufix) {
                this.sufixes.push(sufix);
            },
            removeSufix(sufix) {
                this.sufixes.shift(sufix);
            },
            removePrefix(sufix) {
                this.prefixes.shift(sufix);
            }
        },
        computed: {
            domains() {
                // console.log("generating domains...");
                const domains = [];
                for (const prefix of this.prefixes) {
                    for (const sufix of this.sufixes) {
                        const name = prefix + sufix;
                        const url = name.toLowerCase();
                        const checkout = `https://checkout.hostgator.com.br/?a=add&sld=${url}&tld=.com`;
                        domains.push({
                            name,
                            checkout
                        });
                    }
                }
                return domains;
            }
        }
    };
</script>

<style>
</style>