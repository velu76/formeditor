<template>
	<div>
		<slot></slot>
	</div>
</template>

<script>
export default {
	props: {
		type: { required: true }
	},

	data() {
		return {
		};
	},

}
</script>