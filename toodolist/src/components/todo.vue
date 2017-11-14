<template>
	<li class="todo-line">
		<h3 @mouseenter="showDeleteTag" @mouseleave="hideDeleteTag">
			<input type="checkbox" @click="itemCheck(item)">
			<p class="item-label">{{item}} {{index+1}}</p>
			<p class="item-status" v-if="checked">已完成</p>
			<p class="item-delete" v-if="isShowDeleteTag" @click="deleteClick">delete</p>
		</h3>
	</li>
</template>
<script>
	export default {
		props:["item","index"],
		data(){
			return {
				isShowDeleteTag:false,
				checked:false
			}
		},
		methods:{
			itemCheck(){
				this.checked = !this.checked
			},
			deleteClick(){
				this.$emit('delete', this.index)
			},
			showDeleteTag(){
				this.isShowDeleteTag = true
			},
			hideDeleteTag(){
				this.isShowDeleteTag = false			
			}
		}
	}
</script>
<style scoped>
	.todo-line{
		height:30px;
		line-height:30px;
		list-style:none;
	}
	h3{
		width:400px;
		margin:0 auto;
		color:balck;
		background:gainsboro;
	}
	.item-status{
		display:inline;
		background:red;
		color:#fff;
		padding:0 5px;
		font-size:12px;
	}
	.item-delete{
		display:inline;
		text-decoration:undeline;
		font-size:12px;
		color:gray;
		cursor:pointer;
	}
	.item-label{
		display:inline;
	}
</style>