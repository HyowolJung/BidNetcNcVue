<template>
	<div class="header-main">
		<div class="user-info">
			<div class="text-container">
				<s:authentication property="principal.username" />
				님 환영합니다.
			</div>
			<form method="post" action="/logout">
				<!-- <input
					type="hidden"
					name="${_csrf.parameterName}"
					value="${_csrf.token}"
				/> -->
				<button class="logout-button">로그아웃</button>
			</form>
			<button class="logout-button" onclick="main()">메인화면</button>
		</div>
		<div class="header">
			<a href="">내 정보</a>
			|
			<a href="#" @click="toggleMenu('member')">멤버 관리</a>
			<div v-show="menus.member">
				<RouterLink to="/member/memberList">사원 조회</RouterLink>
				|
				<RouterLink to="/member/memberSearch">사원 검색</RouterLink>
				|
				<RouterLink to="/member/memberInsert">사원 등록</RouterLink>
			</div>
			<!-- <RouterLink to="/member/memberMain">멤버 관리</RouterLink> -->
			<!-- |
			<a href="/project/projectList?pageNo=1">프로젝트 관리</a>
			|
			<a href="">급여 관리</a>
			|
			<a href="">근태 관리</a>
			|
			<a href="">휴가 관리</a>
			|
			<a href="">커뮤니티</a> -->
		</div>
	</div>
</template>
<script>
import { ref } from 'vue';

const menus = ref({
	member: false,
	//project: false,
});

function toggleMenu(menu) {
	menus.value[menu] = !menus.value[menu];
}
</script>

<script setup>
// import { useRouter } from 'vue-router';

// const router = useRouter();
// const goPage = () => {
// 	router.push({
// 		name: 'PostCreate',
// 	});
// };
</script>

<style>
.user-info {
	display: flex;
	justify-content: flex-end; /* 요소들을 오른쪽 끝으로 정렬 */
	align-items: center;
	padding: 5px;
	border-bottom: 1px solid #ccc; /* 테두리 색상 설정 */
	padding-bottom: 10px; /* 하단 간격 추가 */
}

.text-container {
	margin-right: 10px; /* 텍스트와 버튼 사이의 간격 조정 */
}

.logout-button {
	background-color: #007bff;
	color: #fff;
	border: none;
	padding: 5px 9px;
	border-radius: 4px;
	text-decoration: none;
	cursor: pointer;
}

.logout-button:hover {
	background-color: #0056b3;
}

.header,
.footer {
	font-size: 20px;
	text-align: center;
	padding: 10px;
	border-bottom: 1px solid #ccc; /* 테두리 색상 설정 */
	/* padding-bottom: 10px; */ /* 하단 간격 추가 */
}

/* background-color: #f3f3f3; */
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
	border-radius: 5px;
}
/* background-color: #e9ecef; */
.quick-links a,
.header a {
	display: inline;
	margin: 10px 0;
}

a {
	text-decoration-line: none;
}
</style>
