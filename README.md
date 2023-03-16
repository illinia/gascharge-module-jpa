# gascharge-module-jpa

query dsl, spring boot data jpa, h2, json, validation 이 포함된 db 접속 모듈 

기본 설정
* jpa.hibernate.ddl-auto : none
* datasource : 로컬 db 주소
* batch.jdbc.initialize-schema : never (배치 실행시 스키마 생성 안함)
* batch.job.enabled : false (배치 앱 실행시 최초 배치 시작 안함)


* BaseTimeEntity : jpa entity 에서 상속시 생성, 수정 시간 컬럼 추가

*서브 모듈 의존성 없음, 독립적으로 실행 불가능*

query dsl Q클래스 만드는법
```shell
# 중복 생성이 불가능 하다는 에러가 뜨면 src/main/generated 삭제 후 다시 시도
./gradlew compileJava
```

로컬, 원격 메이븐 레포지토리
```groovy
implementation 'com.gascharge.taemin:gascharge-module-jpa:0.0.1-SNAPSHOT'
```

멀티 모듈 프로젝트
```groovy
// settings.gradle
includeProject("jpa", "module")
```
```groovy
// build.gradle
implementation project(":gascharge-module-jpa")
```
YAML 파일 설정은 https://github.com/illinia/gascharge-module-yml 참조