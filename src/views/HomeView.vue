<template>
	<div class="container">
		<p style="text-align: center">환영합니다!</p>
		<form @submit.prevent="handleLogin">
			<div>
				아이디
				<input
					type="text"
					v-model="memberId"
					placeholder="부여받은 사번을 입력하세요."
				/><br />
			</div>
			<br />
			<div>비밀번호 <input type="password" v-model="memberPw" /><br /></div>
			<br />
			<button type="submit">로그인</button>
			<button type="submit" @click="goMainPage">임시 로그인</button>
		</form>
	</div>
	<!-- <div class="container">
		<p style="text-align: center">환영합니다!</p>
		<br /><br />
		<form action="/login" method="post">
			<div>
				아이디
				<input
					type="text"
					id="memberId"
					name="memberId"
					placeholder="부여받은 사번을 입력하세요."
					value="99999999"
				/><br />
			</div>
			<br />
			<div>
				비밀번호
				<input
					type="password"
					id="memberPw"
					name="memberPw"
					value="1234"
				/><br />
			</div>
			<br />
			<button type="submit">로그인</button>
			<input
				type="hidden"
				name="${_csrf.parameterName}"
				value="${_csrf.token}"
			/>
		</form>
		<button class="btn btn-primary" @click="goAboutPage">About으로 이동</button>
	</div> -->
</template>

<script>
import axios from 'axios';

export default {
	data() {
		return {
			memberId: '99999999',
			memberPw: '1234',
		};
	},
	methods: {
		handleLogin() {
			const formData = new FormData();
			formData.append('memberId', this.memberId);
			formData.append('memberPw', this.memberPw);

			axios
				.post('http://localhost:9090/login', this.memberId, this.memberPw)
				.then(response => {
					console.log('Login successful', response);
					alert('로그인 성공');
				})
				.catch(error => {
					console.error('Login failed', error);
					alert('로그인 실패');
				});
		},
	},
};
</script>
<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();
const goMainPage = () => {
	router.push('/main');
};
</script>

<!-- <script setup>
import { useRouter } from 'vue-router';

const router = useRouter();
const goAboutPage = () => {
	router.push('/about');
};
</script> -->

<style>
body {
	font-family: Arial, sans-serif;
	background-color: #f4f4f4;
	color: #333;
	line-height: 1.6;
}

.container {
	max-width: 1000x; /* 최대 너비 설정 */
	margin: 0 auto; /* 가운데 정렬 */
	padding: 20px; /* 패딩 추가 */
	background-color: white; /* 배경색 */
	border-radius: 8px; /* 모서리 둥글게 */
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* 그림자 효과 */
}

input[type='text'],
input[type='password'] {
	width: 100%; /* 너비를 최대로 설정 */
	padding: 8px;
	margin-bottom: 20px; /* 하단 마진 설정 */
	display: inline-block;
	border: 1px solid #ccc; /* 테두리 */
	border-radius: 4px; /* 모서리 둥글게 */
	background: #f1f1f1;
}

button,
.logout-button {
	width: 100%; /* 너비를 최대로 설정 */
	padding: 14px 20px;
	margin-bottom: 20px; /* 하단 마진 설정 */
	border: none;
	border-radius: 4px; /* 모서리 둥글게 */
	cursor: pointer;
}

button:hover,
.logout-button:hover {
	opacity: 0.8;
}
</style>
