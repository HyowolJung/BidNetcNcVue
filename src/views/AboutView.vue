<template>
	<div class="main-content">
		<div class="dashboard">
			<h3>해야할 거</h3>
			<p>1. 3월 13일까지 거래서 제출</p>
			<p>2. 일일결산 밀린거 다하기</p>
		</div>
		<div class="notifications">
			<h3>공지사항</h3>
			<p>사장님의 말씀</p>
			<p>명현이가 전하는 회사소식</p>
		</div>
		<div class="quick-links">
			<h3>바로가기</h3>
			<a href="#">링크 1</a>
			<a href="#">링크 2</a>
			<a href="#">링크 3</a>
		</div>
	</div>
	<div class="footer">
		<p>회사명 | 연락처 정보 | 지원</p>
	</div>
</template>

<script setup>
import { useRoute } from 'vue-router';

const route = useRoute();
console.log('route.path: ', route.path);
</script>

<style>
body {
	font-family: Arial, sans-serif;
}

.main-content {
	display: flex;
	justify-content: space-around;
	margin: 20px;
}

.dashboard,
.notifications,
.quick-links {
	width: 30%;
	padding: 10px;
	background-color: #e9ecef;
	border-radius: 5px;
}
</style>
