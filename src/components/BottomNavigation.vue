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

function handleTabClick(event, index) {
	// console.log(index)
	let icon = event.currentTarget.firstChild
	let rect = icon.getBoundingClientRect()
	console.log(rect)
  selectIndex.value = index
}
</script>

<template>
<div id="wrapper">
	<div id="selectCover"></div>
	<ul>
		<li v-for="(item, index) in tabArrays" :key="item.title" @click.stop="handleTabClick($event, index)">
			<i :class="{select : selectIndex == index}"></i>
			<span v-if="selectIndex == index">
				{{item.title}}
			</span>
		</li>
	</ul>
</div>
</template>

<style scoped>
#wrapper {
	background-color: #EFEFEF;
	display: flex;
	align-items: center;
	justify-content: center;
}

#selectCover {
	width: 60px;
	height: 60px;
	border-radius: 30px;
	background-color: green;
}

ul {
	width: 360px;
	padding: 0;
	list-style-type: none;
	display: flex;
	/* align-items: center; */
	justify-content: center;
	margin-top: 100px;
	padding-top: 50px;
	background-color: white;
	border-radius: 16px;
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
