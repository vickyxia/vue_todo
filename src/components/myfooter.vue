<template>
<div class="myfooter">
	<span>Written by {{author}}</span>
</div>

</template>

<script>
export default{
	data() {
		return {
			author: 'Vicky'
		}
	}
}
</script>
<style >
.myfooter{
	margin-top: 40px;
	text-align: center;
	color: #fff;
	text-shadow: 0 1px 0 rgba(255,255,255,0.5);
	font-size:10px;
}

</style>