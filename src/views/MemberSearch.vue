<template>
	<div class="searchArea">
		<!-- style="display: none;" -->
		<input
			id="pageNo"
			name="pageNo"
			value="${empty pageDto.cri.pageNo ? 1 : pageDto.cri.pageNo}"
			disabled="disabled"
			style="display: none"
		/>
		<select
			name="searchField"
			class="form-select"
			aria-label="Default select example"
			v-model="searchField"
		>
			<option
				v-for="option in options"
				:value="option.value"
				:key="option.value"
			>
				{{ option.text }}
			</option>
		</select>
		<!-- <select name="searchField" class="form-select" aria-label="Default select example" id="searchField">
	  <option value="name" <c:if test = "${pageDto.cri.searchField == 'name' }">selected</c:if>>이름</option>
	  <option value="tel" ${pageDto.cri.searchField == 'tel' ? 'selected' : ''}>전화번호</option>
	</select> -->
		<input
			name="searchWord"
			type="text"
			class="form-control"
			id="searchWord"
			placeholder="검색어"
			value="${pageDto.cri.searchWord }"
		/>
		<label>입사일</label>
		<input
			type="date"
			name="searchDate"
			value="${pageDto.cri.searchStDay}"
			id="searchStDay"
			onblur="validateDate()"
		/>
		~
		<label>퇴사일</label>
		<input
			type="date"
			name="searchDate"
			value="${pageDto.cri.searchLaDay}"
			id="searchLaDay"
			onblur="validateDate()"
		/>

		<button id="searchButton">조회</button>
		<button id="resetButton">초기화</button>
		<button id="downloadButton" onclick="downloadButton()">다운로드</button>
	</div>
	<div>
		<br /><br />
		<table border="1" id="memberTable">
			<thead>
				<tr>
					<th><input type="checkbox" id="checkboxAll" /></th>
					<!-- <th>번호</th> -->
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
					<th style="display: none">프로젝트아이디</th>
					<!-- <th>상태</th> -->
				</tr>
			</thead>
			<tbody></tbody>
		</table>
		<button type="button" value="delete" id="deleteButton">삭제</button>
		<button type="button" value="modify" id="selectButton">수정</button>
		<!-- <button id="insertButton" onclick="insertMember();">등록</button> -->
		<button type="button" value="back" id="backButton">뒤로가기</button>
		<button type="button" value="modify" id="modifyButton">수정</button>
		<div id="pagination">
			<ul class="pagination" style="list-style: none"></ul>
		</div>

		<br /><br /><br />
	</div>
</template>
<script setup>
import { ref } from 'vue';

const searchField = ref('name'); // 초기 선택 값 설정
const options = [
	{ value: 'name', text: '이름' },
	{ value: 'tel', text: '전화번호' },
];
</script>

<script>
export default {
	setup() {
		return {};
	},
};
</script>

<style>
body {
	font-family: 'Arial', sans-serif;
	margin: 20px;
}
.total-div {
	margin-top: 10px;
	margin-left: 230px;
}
.searchArea {
	display: flex;
}

input,
select {
	margin-right: 10px;
}

table {
	border-collapse: collapse;
	width: 100%;
	margin-bottom: 20px;
}

th,
td {
	border: 1px solid #ddd;
	padding: 8px;
	text-align: center;
}

th {
	background-color: #f2f2f2;
}

button {
	padding: 10px;
	cursor: pointer;
}

#pagination {
	margin-top: 20px;
}

ul.pagination {
	display: flex;
	list-style: none;
	padding: 0;
	margin: 0;
}

li.page-item {
	margin-right: 10px;
}

a.page-link {
	text-decoration: none;
	padding: 8px 12px;
	border: 1px solid #ddd;
	color: #333;
	background-color: #fff;
	cursor: pointer;
}

a.page-link.active {
	background-color: #007bff;
	color: #fff;
}

.result-message {
	text-align: center;
	font-style: italic;
	color: #777;
}
.DetailedSearchForm {
	display: none;
}

.total-div {
	margin-top: 20px;
}

.choiceSort,
.selectSort {
	display: inline-block; /* 요소들을 인라인 블록으로 만들어 한 줄에 배치 */
}

.choiceSort button {
	background: none;
	border: none;
	padding: 0;
	cursor: pointer;
}

.selectSort {
	margin-left: 100px; /* choiceSort와 selectSort 사이 간격 */
	/* //margin-left: 50%; */
}

.choiceSort button:hover {
	text-decoration: underline;
}

.choiceSort button,
.selectSort select {
	font-size: 16px; /* 글자 크기 */
	margin: 5px; /* 버튼과 셀렉트 박스 주변 여백 */
}
input,
select {
	margin-right: 10px;
}

table {
	border-collapse: collapse;
	width: 100%;
	margin-bottom: 20px;
}

th,
td {
	border: 1px solid #ddd;
	padding: 8px;
	text-align: center;
}

th {
	background-color: #f2f2f2;
}

button {
	padding: 10px;
	cursor: pointer;
}

#pagination {
	margin-top: 20px;
}

ul.pagination {
	display: flex;
	list-style: none;
	padding: 0;
	margin: 0;
}

li.page-item {
	margin-right: 10px;
}

a.page-link {
	text-decoration: none;
	padding: 8px 12px;
	border: 1px solid #ddd;
	color: #333;
	background-color: #fff;
	cursor: pointer;
}

a.page-link.active {
	background-color: #007bff;
	color: #fff;
}

.result-message {
	text-align: center;
	font-style: italic;
	color: #777;
}
</style>
