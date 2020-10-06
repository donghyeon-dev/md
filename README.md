### **Publishing 진행 계획 보고서**


>**목차**


>1. 스타일(scss) 적용 방법
>2. 네이밍 계획
>3. 진행순서


----------


## 스타일(scss) 적용 방법
================================================

먼저, 일반 css가 아닌 scss를 적용하기 위해선
< style > 태그에 lang="scss"를 추가한다.
>**ex)**
>< style  **lang="scss"**> 
> div{ width:100px; }
>< /style >


---------------
####**1. 개별 css적용.**


필요한 컴포넌트마다 로컬단위로 적용.
개별css 적용시 style 태그 내에 **scoped** 속성을 추가해 현재 컴포넌트에만 특정 스타일을 적용한다.


> **import 방법**

>< script >
	export default {
		name: '',
		data: {}
		// …
	}
< /script >
< style **scoped** lang="scss">
	label {
		display: inline-block;
		align-items: center;
		cursor: pointer;
		}
</style >

** 태그안에 **@import** 를 해야함

---------------
####**2. 공통 css적용.**


루트 컴포넌트에서  global scss를 적용.
main.js와 같은 엔트리 포인트에서 로드하는 루트 컴포넌트에서 *(ex.App.vue)* 
전역으로 사용하는 scss를 import하여 적용한다.

> **import 방법**

>< script >
	export default {
		name: '',
		//..
	}
< /script >
< style lang="scss" >
	**@import './경로';** 
< /style >

** 태그안에 **@import** 를 해야함

----------


#####+ 추가  **Deep Selector**

scoped 속성을 부여하면 해당 컴포넌트에만 적용이 되는데, 최상위 태그에만 적용이 된다.
이럴 때, ::v-deep(또는 '>>>', '/deep/') 을 사용해서 접근해야 한다.

**일반 css 가 아닌 sass 등의 전처리기는 [>>>] 구문을 제대로 분석하지 못할 수 있기때문에
 **/deep/** 이나 **::v-deep** 결합기를 사용한다.
둘 다 [>>>] 와 동일하게 작용한다.

>**ex)**
>< style lang="scss" scoped>
**::v-deep** .aa {
  .a {
    top: 20px;
  }
}
< /style>

>**or**
>< style scoped >
.aa **>>>** .a {
    top: 20px;
}
< /style >

>**or**
>< style lang="scss" scoped>
**/deep/** .a {
  background: red;
}
< /style >



자주 사용하는 속성은  utility class로 만들어 손쉽게 재사용 할 수 있게끔 한다.*(=부트스트랩같은 역할)*


================================================
## 네이밍 계획
================================================

아이디명은 "_" (언더바),
클래스명은 " - " (하이폰)을 사용하여 구분.

네이밍은 BEM 방식으로 진행하되, 최대한 간략히 공통으로 묶어 사용할 수 있는 방향으로 진행하면 좋을듯함

>B - block ( nav, menu, header, search-form, main etc..)
E - elements (input,  first,  logo, inner, frame, title, text, item etc..)
M - modifiers ( blue, red, small, big, disabled etc..)

---


## 진행 계획
================================================
![업무 프로세스](https://user-images.githubusercontent.com/72370405/95160935-bd983300-07dc-11eb-8a30-3b1e32d80f19.png)

