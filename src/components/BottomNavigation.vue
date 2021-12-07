<script setup>
import { ref } from 'vue'

defineProps({
  msg: String
})

const selectIndex = ref(0)
const tabArrays = ref([
  {
	title: '首页',
	icon: 'home',
  },
  {
	title: '广场',
	icon: 'square',
  },
  {
	title: '购物',
	icon: 'shopping',
  },
  {
	title: '个人',
	icon: 'profile',
  }
]) 

function handleTabClick(index) {
	console.log(index)
  selectIndex.value = index
}
</script>

<template>
<div>
	<ul>
		<li v-for="(item, index) in tabArrays" :key="item.title" @click="handleTabClick(index)">
			<i :class="{select : selectIndex == index}"></i>
			<span v-if="selectIndex == index">
				{{item.title}}
			</span>
			<!-- <i class="iconfont" :class="item.icon"></i>
			<span>{{item.title}}</span> -->
		</li>
	</ul>
</div>
</template>

<style scoped>
div {
	background-color: #EFEFEF;
	display: flex;
	align-items: center;
	justify-content: center;
}

ul {
	width: 320px;
	padding: 0;
	list-style-type: none;
	display: flex;
	/* align-items: center; */
	justify-content: center;
	margin-top: 100px;
	padding-top: 50px;
	background-color: white;
}

li {
	width: 80px;
	height: 80px;
	display: flex;
	flex-direction: column;
	align-items: center;
	/* justify-content: center; */
	cursor: pointer;
	font-family: 'Ping Fang SC', 'PingFang SC', 'PingFang', 'Microsoft YaHei', 'Helvetica Neue', Helvetica, Arial, sans-serif;
}

/* li::before {
	content: "";
	width: 40px;
	height: 40px;
	background-color: gray;
	border-radius: 4px;
} */
i {
	width: 40px;
	height: 40px;
	background-color: gray;
	border-radius: 4px;
	transform: translateY(10px);

	transition: transform 0.3s;
}

.select {
	/* translate: 0, -50px; */
	transform: translateY(-20px);
}
</style>
