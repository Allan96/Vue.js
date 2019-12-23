<template>
  <div>
    <h5>{{title}} <span class="badge badge-info">{{ items.length }}</span></h5>
          <div class="card">
             <div class="card-body">
              <ul class="list-group">
                <li class="list-group-item" v-for="item in items" v-bind:key="item">
                  <div class="row">
                    <div class="col-md">
                      {{ item }}
                    </div>
                    <div class="col-md text-right">
                      <button type="button" class="btn btn-info" v-on:click="removeItem(item)"><i class="fa fa-trash" aria-hidden="true"></i> </button>
                    </div>
                  </div>
                </li>
              </ul>
              <br/>
              <div class="input-group">
                <input type="text" class="form-control" v-model="item"  v-on:keyup.enter="addItem(item)" placeholder="Digite o Item" />
                <div class="input-group-append">
                  <button type="button" class="btn btn-info" v-on:click="addItem(item)"> <i class="fa fa-plus" aria-hidden="true"></i> </button>
                </div>
              </div>
            </div>
        </div>
  </div>
</template>

<script>
export default {
	name: "AppItemList",
  props: ["title", "items"],
  data(){
    return {
      item: ""
    }
  },
  methods:{
    addItem(item){
      this.$emit("addItem", item);
      this.item = "";
    },
     removeItem(item){
      this.$emit("removeItem", item);
      this.item = "";
    }
  }
};
</script>
<style scoped>
</style>
