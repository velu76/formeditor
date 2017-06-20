<template>
<div>
  
      <div class="tile is-vertical is-3">
        <div class="tile">
          <div class="tile is-parent is-vertical">
            <article class="tile is-child notification is-primary">
              <h1>Tools</h1>                      
              <ul>
              	<li v-for="tool in tools">
              		<button class="btn" @click="$emit('addToForm',tool.type)"> {{ tool.type.toUpperCase() }} </button> 
              	</li>
              </ul>
            </article>                  
          </div>
        </div>
      </div>

   <div class="tool-details">
   	<slot></slot>
   </div>

</div>
</template>

<style>
	.btn {
		width: 140px;
	}
</style>

<script>
export default {
	data() {
		return {
			tools: []
		};
	},

	mounted() {
		this.tools = this.$children;
	}

}
</script>