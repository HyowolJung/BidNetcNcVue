<template>
	<h2>MemberList.vue</h2>
	<div class="choiceSort">
		<button id="IdUp" @click="IdUpList" value="IdUp">사번 높은 순</button>
		<!-- |
		<button id="IdDown" onclick="getMemberList(this)" value="IdDown">
			사번 낮은 순
		</button>
		|
		<button id="DeptUp" onclick="getMemberList(this)" value="DeptUp">
			직급 높은 순
		</button>
		|
		<button id="DeptDown" onclick="getMemberList(this)" value="DeptDown">
			직급 낮은 순
		</button>
		|
		<button id="RecentStDay" onclick="getMemberList(this)" value="RecentStDay">
			최근 입사 순 
		</button>-->
	</div>
	<div>
		<table border="1" id="memberTable">
			<thead>
				<tr>
					<th>사번</th>
					|
					<th>이름</th>
					|
					<th>성별</th>
					|
					<th>부서</th>
					|
					<th>직책</th>
					|
					<th>직급</th>
					|
					<th>전화번호</th>
					|
					<th>입사일</th>
					|
					<th>퇴사일</th>
					|
					<th>상태</th>
				</tr>
			</thead>
			<tbody>
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
			</tbody>
			<tr v-if="memberList.length === 0">
				<td colspan="10" style="text-align: center">결과가 없어요.</td>
			</tr>
		</table>
	</div>
</template>

<script>
import axios from 'axios';

export default {
	data() {
		return {
			memberList: [],
		};
	},

	methods: {
		IdUpList() {
			axios
				.post('member/memberList')
				.then(response => {
					this.members = response.data;
					console.log('response.data', response.data);
				})
				.catch(error => {
					console.error('멤버 불러오기 실패', error);
				});
		},
	},
};
</script>
