<template>
<div class="modal is-active">
  <div class="modal-background"></div>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">Properties</p>
      <button class="delete" @click="$emit('close')"></button>
    </header>
    <section class="modal-card-body">
    	<label for="labelText">Label Name</label>
       	<input type="text" name="txtinput" id="txtinput" v-model="p_lname">       
		<hr>
       	<label for="labelText">Input name</label>
       	<input type="text" name="txtinput" id="txtinput" v-model="p_name">  
       	<hr>
       	<label for="labelText">Input size length</label>
       	<input type="text" name="txtinput" id="txtinput" v-model="p_size">       
       	
    </section>
    <footer class="modal-card-foot">
      <a class="button is-success" @click="saveProperties">Save changes</a>
      <a class="button" @click="$emit('close')">Cancel</a>
    </footer>
  </div>
</div>
</template>

<script>
	export default {
		props: {
			name:  { required: true },
			lname: { required: true },
			tsize:  { required: true }
		},

		data() {
			return {
				p_name : this.name,
				p_lname : this.lname,
				p_size : this.tsize
			};
		},

		methods: {
			saveProperties() {
				this.$emit('updateProperties', this.p_name, this.p_lname, this.p_size);
			},
		}		
	}
</script>