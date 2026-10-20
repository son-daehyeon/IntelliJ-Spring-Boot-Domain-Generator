# IntelliJ-Spring-Boot-Domain-Generator

> 단축키로 Spring Boot CRUD 도메인 패키지를 만드는 IntelliJ 플러그인

Spring Boot 프로젝트에서 도메인을 추가할 때마다 반복되는 Controller·Service·Entity·Repository·DTO·Exception 작성을 대신해 주는 IntelliJ IDEA 플러그인이다. 도메인 이름과 속성 목록을 입력하면 CRUD 코드가 들어 있는 패키지를 만든다. [Spring-Security-MySQL-JWT-Template](https://github.com/son-daehyeon/Spring-Security-MySQL-JWT-Template) 구조에 맞춰 2025년에 만들었고, JetBrains Marketplace에 "Spring Boot Domain Generator"로 올라가 있다.

## 주요 기능
- `domain` 패키지에서 `Ctrl + Shift + S` 또는 우클릭 → "New Spring Boot Domain"으로 생성 다이얼로그 열기
- 다이얼로그에서 도메인명과 속성(이름, 타입, Nullable, 상세 조회 시 표시 여부)을 표로 입력
- 도메인명·속성명·타입 형식과 중복 속성명 검사
- 생성 파일
  - `controller/{Name}Controller.java`: 목록·단건 조회, 생성, 수정, 삭제 엔드포인트
  - `service/{Name}Service.java`
  - `entity/{Name}.java`: 템플릿의 `BaseSchema`를 상속하는 JPA 엔티티
  - `repository/{Name}Repository.java`: `JpaRepository<{Name}, UUID>`
  - `dto/`: `Upsert{Name}Request`, `{Name}Response`, `Simple{Name}Response`, `{Name}ListResponse`
  - `exception/{Name}Exceptions.java`

## 기술 스택
| 영역 | 기술 |
|---|---|
| 언어 | Kotlin 2.1.0 (JVM 11) |
| 프레임워크 | IntelliJ Platform Gradle Plugin 2.5.0, IntelliJ IDEA 2023.1 ~ 2025.1 (빌드 231 ~ 251.*) |
| 라이브러리 | evo-inflector 1.3 |

## 구조
```
src/main/kotlin/com/github/son_daehyeon/spring_boot_domain_generator/
├── action/GenerateDomainAction.kt    단축키·메뉴 액션, 입력 검증
├── dialog/DomainGeneratorDialog.kt   도메인명·속성 입력 다이얼로그
├── generator/                        Controller·Service·Entity·Repository·DTO·Exception 코드 생성
└── model/DomainInfo.kt               도메인·속성 모델
src/main/resources/META-INF/plugin.xml
```

## 실행
IntelliJ IDEA → Settings → Plugins → Marketplace에서 "Spring Boot Domain Generator"를 검색해 설치하거나, [Releases](https://github.com/son-daehyeon/IntelliJ-Spring-Boot-Domain-Generator/releases)에서 내려받는다. 소스에서 플러그인을 띄워 보려면 다음을 실행한다.

```bash
./gradlew runIde
```
[Spring-Security-MySQL-JWT-Template](https://github.com/son-daehyeon/Spring-Security-MySQL-JWT-Template) 기반 프로젝트의 `domain` 폴더에서 써야 한다.

## 관련 저장소
- [Spring-Security-MySQL-JWT-Template](https://github.com/son-daehyeon/Spring-Security-MySQL-JWT-Template) — 생성 코드가 맞춰진 기반 템플릿

---
2025 · 개인 프로젝트 · 보관됨
