<template>
	<div class="txtbox">
		<span>		
			<label for="text" @click="updateLabel">{{ lname }}</label>
			<input type="text" :id="name" :size="tsize">
			<span><button class="btn-close" @click="removeMe">x</button></span>
			<span><button class="btn-close" @click="showWindow=true">e</button></span>
			<span><a class="btn">m</a></span>

			<text-props-window 
				v-show="showWindow" 
				@close="showWindow=false" 
				@updateProperties='updateMe'
				:name="name" 
				:lname="lname"
				:tsize ="tsize">			
			</text-props-window>
		</span>	
	</div>
	
</template>

<style>
	.txtbox {
		padding: 5px 5px;
		border: 1px solid #e5e5e5;
		margin-bottom: 5px;		
	}
	
	.txtbox label {
		padding-right: 5px;
		font-style: italic;
	}

	.btn-close {
		background: #1c5e5e;
		color: #ffffff;
	}

	

</style>

<script>
import TextPropsWindow from './text-props-window.vue';
	export default {
		data() {
			return {				
				name: '',
				lname: 'Custom Label',
				tsize: 60,
				showWindow: false				
			};
		},

		components: {
			TextPropsWindow
		},

		methods: {
			updateLabel() {
				this.lname = prompt("Label's new value", this.lname);
				this.name = this.lname;
			},

			updateMe(pname, plname, tsize){
				this.name = pname;
				this.lname = plname;
				this.tsize = tsize;
				this.showWindow = false;
			},

			removeMe() {
				this.$emit('removeMe');
			}

		},
		
	}
</script>