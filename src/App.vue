<template>
  <div id="app">     
    <div class="tile is-ancestor">      
        
      <fb-tools @addToForm="newItem">
        <fb-tool type="text"></fb-tool>
        <fb-tool type="email"></fb-tool>
        <fb-tool type="date"></fb-tool>
        <fb-tool type="datetime"></fb-tool>
      </fb-tools>    

    <div class="tile is-vertical is-9 edit-window" >
      <div class="tile">
        <div class="tile is-parent is-vertical">
          <article class="tile is-child box is-info">
            <h2 class="hh2">Form editor</h2>      
            <template v-for="(view,id)  in views" >
              <component  :is="view.name" :key="view.id" :id="view.id" @removeMe="remove(id)"></component>
            </template>                    
          </article>                  
        </div>
      </div>
    </div>          


    </div>
    
  </div>
</template>

<style>
#app {
  padding:20px 20px;
}

.hh2 {
  font-size: 0.9em;
  color: #c2c2c2;
}

.edit-window {
  height:800px;
}
</style>

<script>
import FbTools  from  './components/fb-tools.vue';
import FbTool   from  './components/fb-tool.vue';
import FbtText  from  './components/fbt-text.vue';
export default {
  name: 'app',

  methods: {
    newItem(data) {
      if(data == 'text'){    
        this.views.push({name: 'fbt-text', id: this.ref_id}) ;
        this.ref_id += 1
      }
    },  
    remove(id) {
     this.views.splice(id,1);
    }  
  },

  components: {
      FbTools,
      FbTool,
      FbtText
  },
  data () {
    return {   
      views: [],
      ref_id: 0,
    };
  }
}
</script>