
패키지란?

**npm의 원칙**
- 여러 버전의 동일한 패키지를 한 프로젝트에서 사용할 수 있게 하자
- 설치 방식을 통일하자
- 패키지 관련 정보가 들어있는 메타 데이터를 간소화 하자
- 누구나 배포할 수 있도록 하자

npm directory
node_modules : 설치한 패지
package.json : 패키지를 다룰 수 있는 cli 및 메타데이터
package-lock.json
.npmrc


**yarn: yet another resource negotiator**
- 병렬화를 통한 속도 개선
- 자동화 된 Lock 생성
- 의존성 트리 알고리즘 변경
- 캐시 사용
- 

**yarn directory**
.yarn
 cache/
 releases/
	 yarn-1.22.17.cjs
node_modules
.yarnrc
package.json
yarn.lock

**npm의 한계**
- 비효율적 의존성 검색

![[Pasted image 20240131234807.png]]

- package.json엔 명시가 안되는 문제
- 너무 무거운 node_modules



**Pnpm**

- 평탄화 되지 않은 node_modules
![[Pasted image 20240131235007.png]]


링크를 사용한 효과적인 패키지 연결
![[Pasted image 20240131235148.png]]


**yarn v2**
yarn set version berry

node_modules 와 node에 내장된 의존성 관리 없이 의존성을 관리하면 어떨까?
![[Pasted image 20240131235252.png]]



![[Pasted image 20240131235316.png]]

yarn v2 - plug'n'play

![[Pasted image 20240131235439.png]]
