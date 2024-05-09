<template>
	<div class="choiceSort">
		<!-- <button @click="fetchMemberLists">post 데이터 소환</button> -->
		<button @click="fetchMemberLists('IdUp')">사번 높은 순</button>
		<button @click="fetchMemberLists('IdDown')">사번 낮은 순</button>
		<button @click="fetchMemberLists('DeptUp')">직급 높은 순</button>
		<button @click="fetchMemberLists('DeptDown')">직급 낮은 순</button>
		<button @click="fetchMemberLists('RecentStDay')">최근 입사 순</button>
	</div>
	<div>
		<table border="1" id="memberTable" width="100%">
			<thead>
				<tr>
					<th>사번</th>
					<th>이름</th>
					<th>성별</th>
					<th>부서</th>
					<th>직책</th>
					<th>직급</th>
					<th>전화번호</th>
					<th>입사일</th>
					<th>퇴사일</th>
					<th>상태</th>
				</tr>
			</thead>
			<tbody>
				<!-- 데이터가 있을 경우 각 멤버 정보를 표시 -->
				<tr v-for="member in memberList" :key="member.memberId">
					<td>{{ member.memberId }}</td>
					<td>{{ member.memberName }}</td>
					<td>{{ member.memberGn }}</td>
					<td>{{ member.memberDept }}</td>
					<td>{{ member.memberRo }}</td>
					<td>{{ member.memberPos }}</td>
					<td>{{ member.memberTel }}</td>
					<td>{{ member.memberStDay }}</td>
					<td>{{ member.memberLaDay }}</td>
					<td>{{ member.memberSt }}</td>
				</tr>
				<!-- 데이터가 없을 경우 '결과가 없어요.' 메시지 표시 -->
				<tr v-if="memberList.length === 0">
					<td colspan="10" style="text-align: center">결과가 없어요.</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>

<style>
table {
	width: 100%; /* 테이블의 너비를 전체로 설정 */
	border-collapse: collapse; /* 테이블의 경계선을 겹치게 함 */
}

th,
td {
	border: 1px solid black; /* 경계선 스타일 */
	text-align: left; /* 텍스트 정렬 */
	padding: 8px; /* 내부 여백 */
}

th {
	background-color: #f2f2f2; /* 배경색 설정 */
}
.choiceSort {
	display: flex; /* 플렉스박스 레이아웃 사용 */
	justify-content: space-around; /* 버튼 사이에 공간 동일하게 분배 */
}

.choiceSort button {
	flex: 1; /* 모든 버튼이 가용 공간을 동일하게 차지하도록 설정 */
	margin: 5px; /* 버튼 사이의 마진 설정 */
	padding: 10px 0; /* 버튼의 상하 패딩 설정 */
	text-align: center; /* 텍스트 중앙 정렬 */
}
</style>
<style scoped>
.choiceSort {
	display: flex;
	justify-content: space-around;
}

.choiceSort button {
	flex: 1;
	margin: 5px;
	padding: 10px 0;
	text-align: center;
}
</style>
<script>
import axios from 'axios';

export default {
	data() {
		return {
			//members: [],
			memberList: [],
			pageNo: 1,
			amount: 5,
		};
	},
	methods: {
		fetchMemberLists(choiceValue) {
			const cri = {
				choiceValue: choiceValue,
				pageNo: this.pageNo,
				amount: this.amount,
			};
			axios
				.post('http://localhost:5000/member/memberList', cri)
				.then(response => {
					if (response.data && Array.isArray(response.data.memberList)) {
						this.memberList = response.data.memberList;
						console.log('response.data.memberList', response.data.memberList);
					} else {
						throw new Error('Invalid response structure');
					}
				})
				.catch(error => {
					console.error('Error fetching members:', error);
					this.memberList = []; // 오류 발생 시 리스트를 비워 오류를 방지
					alert('Failed to fetch member data.');
				});
		},
	},
};
</script>
