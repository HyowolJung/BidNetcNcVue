<template>
	<div>MemberInsert.vue</div>
	<div class="total-div">
		<div class="container">
			<div class="column" style="text-align: left">
				<p style="color: red; text-align: center">필수 입력</p>

				<label style="color: red">사번</label>
				<input type="text" id="memberId" /><br />
				<div id="result_Id"></div>

				<label style="color: red">비밀번호</label>
				<input type="text" id="memberPw" value="1234" /><br />
				<div id="result_Pw"></div>

				<label style="color: red">이름</label>
				<input type="text" id="memberName" value="안녕" /><br />
				<div id="result_Name"></div>

				<label style="color: red"
					>전화번호<br />
					("-"포함)</label
				>
				<input type="text" id="memberTel" /><br />
				<div id="result_Tel"></div>
				<br />

				<label style="color: red">입사(예정)일</label>
				<input
					type="date"
					id="member_startDate"
					name="memberStDay"
					value="2024-03-10"
				/><br />
				<div id="result_Date"></div>
			</div>
		</div>
		<div class="container">
			<div class="column" style="text-align: left">
				<p style="text-align: center">선택 입력</p>

				<label>부서</label>
				<select id="memberDept">
					<option value="" selected="selected">선택</option>
					<option value="D01">경영지원부</option>
					<option value="D02">인사부</option>
					<option value="D03">IT부</option>
					<option value="D04">재무부</option>
					<option value="D05">회계부</option>
					<option value="D06">마케팅부</option></select
				><br /><br />

				<label>직급</label>
				<select id="memberPos">
					<option value="" selected="selected">선택</option>
					<option value="P01">회장</option>
					<option value="P02">부회장</option>
					<option value="P03">사장</option>
					<option value="P04">부사장</option>
					<option value="P05">전무</option>
					<option value="P06">상무</option>
					<option value="P07">본부장</option>
					<option value="P08">실장</option>
					<option value="P09">팀장</option>
					<option value="P10">부장</option>
					<option value="P11">차장</option>
					<option value="P12">과장</option>
					<option value="P13">대리</option>
					<option value="P14">주임</option>
					<option value="P15">사원</option>
					<option value="P16">인턴</option></select
				><br /><br />

				<label>성별</label>
				<select id="memberGn">
					<option value="" selected="selected">선택</option>
					<option value="G01">남자</option>
					<option value="G02">여자</option></select
				><br /><br />

				<label>자격증</label>

				<!-- <label>언어</label>
	<select id="member_Skill_Language">
		<option value="" selected="selected">선택</option>
		<option value="S010">JAVA</option>
		<option value="S011">PYTHON</option>
		<option value="S012">C++</option>
		<option value="S013">RUBY</option>
	</select><br><br>
	
	<label>데이터베이스</label>
	<select id="member_Skill_DB">
		<option value="" selected="selected">선택</option>
		<option value="S020">ORACLE</option>
		<option value="S021">MSSQL</option>
		<option value="S022">MYSQL</option>
		<option value="S023">POSTGRESQL</option>
	</select><br><br> -->
			</div>
		</div>
		<div class="buttons">
			<button type="button" value="insert" id="insert">추가</button>
			<button type="button" value="back" id="back">뒤로 가기</button>
		</div>
	</div>
</template>

<script>
export default {
	setup() {
		return {};
	},
};
</script>

<style>
body {
	/* font-family: 'Arial', sans-serif; */
	/* background-color: #f4f4f4; */
	margin: 0;
	padding: 20px;
}

/* 각 column에 대한 스타일 */
.column {
	background-color: #fff;
	border-radius: 5px;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	padding: 20px;
	margin-bottom: 20px;
}

/* 필수 입력과 선택 입력의 제목 스타일 */
.column p {
	color: #333;
	font-weight: bold;
	text-align: left;
	margin-top: 0;
}

/* 레이블 스타일 */
label {
	color: #333;
	display: block;
	margin-bottom: 5px;
}

/* 필수 입력 항목의 레이블에 대한 스타일 */
label[style='color: red'] {
	color: #d9534f;
}

/* input 및 select 박스 기본 스타일 */
input[type='text'],
input[type='date'],
select {
	width: 100%;
	padding: 10px;
	margin-bottom: 10px;
	border: 1px solid #ccc;
	border-radius: 4px;
	box-sizing: border-box; /* 박스 사이즈를 지정해서 패딩이 width에 포함되도록 함 */
}

/* 버튼 스타일 */
button {
	background-color: #4caf50; /* 녹색 */
	color: white;
	padding: 14px 20px;
	margin: 8px 0;
	border: none;
	border-radius: 4px;
	cursor: pointer;
	width: 100%;
}

button:hover {
	background-color: #45a049;
}

/* 반응형 디자인: 화면 너비가 600px 미만일 때 column과 버튼 사이즈 조정 */
@media screen and (max-width: 600px) {
	.column,
	button {
		width: 100%;
	}
}

/* 결과 메시지 스타일 */
#result_Id,
#result_Pw,
#result_Name,
#result_Tel,
#result_Date {
	color: #d9534f;
	font-size: 0.9em;
}

/* 필수 입력 부분의 제목 색상 */
.column:first-child p {
	color: #5cb85c; /* 연한 녹색 */
}
.container {
	/* width: 30%;  or 원하는 폭에 맞게 조정 */
	margin: auto; /* 좌우 마진을 auto로 설정하여 가운데 정렬 */
	background-color: #fff; /* 배경색을 흰색으로 설정 */
	padding: 20px;
	border-radius: 8px; /* 모서리를 둥글게 */
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2); /* 상자 그림자를 추가하여 입체감을 줍니다 */
}

/* .column 스타일은 유지하되, 중앙 정렬이 필요없으므로 margin-bottom만 설정합니다. */
.column {
	padding: 20px;
	margin-bottom: 20px; /* 컬럼 사이의 간격 */
}

/* 섹션 제목을 중앙 정렬합니다. */
.column p {
	text-align: center;
}

/* 버튼 컨테이너를 추가하여 버튼을 가운데로 정렬합니다. */
.buttons {
	text-align: center; /* 버튼을 중앙에 정렬 */
	padding: 20px 0;
}

/* 버튼을 인라인 블록으로 변경하여 가운데 정렬되도록 합니다. */
button {
	width: auto; /* 버튼의 너비를 내용에 맞게 조정 */
	display: inline-block; /* 인라인 블록으로 설정 */
	margin: 0 10px; /* 좌우 마진을 줘서 버튼 사이에 간격을 추가 */
}

/* 반응형 디자인을 위한 미디어 쿼리 */
@media screen and (max-width: 768px) {
	.container {
		width: 95%;
	}
}

/* 추가로, 필요하다면 개별 입력 필드의 너비를 조정할 수 있습니다. */
input[type='text'],
input[type='date'],
select {
	width: calc(100% - 20px); /* 입력 필드의 좌우 패딩을 고려하여 조정 */
}
</style>
