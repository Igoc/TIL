## Spring Data JPA

Spring에서 JPA를 편리하게 사용할 수 있도록 해주는 모듈로, 인터페이스 상속만으로 Repository를 구현할 수 있게 해준다.

### 라이브러리 설치

#### Gradle

```
implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
```

### SQL 쿼리문 출력

application.properties 파일 안에 다음의 내용을 추가해주면 된다.

```
spring.jpa.show-sql=true
```

### 예제

#### Course (Entity)

``` java
// JPA Entity 생성
@Entity
public class Course {

    // id 필드를 데이터베이스의 id 열에 매핑하고, 값이 자동으로 증가되는 기본 키로 설정
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;

    // title 필드를 데이터베이스의 title 열에 매핑하고, 항상 값이 존재하도록 설정
    @Column(nullable = false)
    private String title;

    // tutor 필드를 데이터베이스의 tutor 열에 매핑
    @Column
    private String tutor;

    public Course() {}

    public Course(String title, String tutor) {
        this.title = title;
        this.tutor = tutor;
    }

    public void update(CourseDto courseDto) {
        title = courseDto.getTitle();
        tutor = courseDto.getTutor();
    }

    public String getId() {
        return id;
    }

    public String getTitle() {
        return title;
    }

    public String getTutor() {
        return tutor;
    }

}
```

#### CourseDto (DTO)

``` java
public class CourseDto {

    private String title;
    private String tutor;

    public CourseDto(String title, String tutor) {
        this.title = title;
        this.tutor = tutor;
    }

    public String getTitle() {
        return title;
    }

    public String getTutor() {
        return tutor;
    }

}
```

#### CourseRepository (Repository)

``` java
// 기본 키 자료형이 Long인 Course Entity를 사용하는 Repository 생성
public interface CourseRepository extends JpaRepository<Course, Long> {}
```

#### CourseService (Service)

``` java
@Service
public class CourseService {

    private final CourseRepository repository;

    public CourseService(CourseRepository repository) {
        this.repository = repository;
    }

    // 트랜잭션 처리
    @Transactional
    public Long update(Long id, CourseDto courseDto) {
        Course course = courseRepository.findById(id).orElseThrow(
                () -> new IllegalArgumentException("존재하지 않는 아이디")
        );

        course.update(courseDto);

        return course.getId();
    }

}
```

#### Application

``` java
@SpringBootApplication
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

    @Bean
    public CommandLineRunner example(CourseRepository repository, CourseService service) {
        return (args) -> {
            // 데이터 삽입
            repository.save(new Course("강의 A", "튜터 A"));
            repository.save(new Course("강의 B", "튜터 B"));

            // 데이터 조회
            List<Course> courses = repository.findAll();

            for (Course course : courses) {
                System.out.println(course.getId());
                System.out.println(course.getTitle());
                System.out.println(course.getTutor());
            }

            // ID로 데이터 조회
            Course course = courseRepository.findById(1L).orElseThrow(
                    () -> new IllegalArgumentException("존재하지 않는 아이디")
            );

            // 데이터 수정
            service.update(1L, new CourseDto("강의 A", "튜터 C"));

            // ID로 데이터 삭제
            repository.deleteById(1L);
        };
    }

}
```

``` bash
[출력]
1
강의 A
튜터 A
2
강의 B
튜터 B
```

### @MappedSuperclass

여러 Entity에서 공통으로 매핑되는 필드를 갖는 클래스를 정의하기 위한 어노테이션이다.

#### 예제

##### Timestamp

``` java
// 여러 Entity에서 사용할 수 있도록 JPA Auditing이 적용된 타임스탬프를 생성
@MappedSuperclass
@EntityListeners(AuditingEntityListener.class)
public abstract class Timestamp {

    // 생성일자를 나타내는 필드로 데이터베이스의 created_date 열에 매핑
    @CreatedDate
    private LocalDateTime createdDate;

    // 마지막 수정일자를 나타내는 필드로 데이터베이스의 last_modified_date 열에 매핑
    @LastModifiedDate
    private LocalDateTime lastModifiedDate;

}
```

##### Course (Entity)

``` java
@Entity
public class Course extends Timestamp { ... }
```

##### Application

``` java
// JPA Auditing 활성화
@SpringBootApplication
@EnableJpaAuditing
public class Application { ... }
```