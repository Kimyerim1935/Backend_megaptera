## ✔️ 키워드 정리

### DAO(Data Access Object)

DAO는 Database에 접근하는 역할을 하는 객체이다. 데이터의 CRUD 작업을 시행하는 클래스(데이터에 대한 CRUD 기능을 전담하는 오브젝트)라고 볼 수 있다.

프로그램을 모듈화하는 가장 일반적인 방법 중 하나는 프레젠테이션(UI),도메인 로직(비즈니스 로직), 데이터 액세스 라는 세 가지 계층으로 분리하는 것이다.

웹 애플리케이션은 

1. HTTP 요청을 처리하고 HTML을 렌더링하는 웹 계층
2. 유효성 검사 및 계산을 포함하는 비즈니스 계층
3. 데이터베이스 또는 원격 서비스에서 영구 데이터를 관리하는 방법을 분류하는 데이터 액세스 계층

으로 나뉘는 경우가 많다.

모듈화의 가장 큰 장점은 세 가지의 주제를 비교적 독립적으로 생각할 수 있어, 주의의 범위를 줄일 수 있다는 점이다.

요소를 분리하면 각 요소에 대한 생각의 범위가 좁아져 필요한 작업을 더 쉽게 할 수 있다는 장점이 있다.

이런식으로 사용하면 된다.

```java
public class PostService {
    
    private final PostDAO postDAO;


    public PostService(){
        this.postDAO = new PostDAO;
    }

    public List<PostDto> getPostDtos(){
        return postDAO.findAll();
    }

    public PostDto getPostDto(String id){
        return postDAO.find(id);
    }

    public PostDto createPost(PostDto postDto){
        String id = TsidCreator.getTsid().toString();

        PostDto newPostDto = new PostDto();
        newPostDto.setId(id);
        newPostDto.setTitle(postDto.getTitle());
        newPostDto.setContent(postDto.getContent());

        postDAO.save(newPostDto);
      
        return newPostDto;
    }
}

public class PostDAO{
    private final List<PostDto> postDtos;

    public PostDAO() {
        this.postDtos =  new ArrayList();

        this.postDtos.add(new PostDto("1","제목","테스트입니다"));
        this.postDtos.add(new PostDto("2","제목2","테스트2입니다"));
    }

    public List<PostDto> findAll(){
        return new ArrayList<>(postDtos);
    }

    public PostDto find(String id){
        return postDtos.stream().filter(post -> post.getId().equals(id)).findFirst().onElseThrow(PostNotFound::new);
    }

    public void save(PostDto postDto){
       postDtos.add(postDto);
    }

}
```

### List

[List](https://docs.oracle.com/javase/8/docs/api/java/util/List.html)를 사용하면 각 요소가 삽입되는 위치를 정확하게 제어할 수 있다.

객체 자체를 저장하는 것이 아니라 주소를 참조하며 `null`을 담을 수 있고, 데이터의 중복을 허용(동일한 주소를 참조)한다.

### Map

key를 value에 매핑하는 객체이다. 중복 키가 포함될 수 없으며, 각 키는 최대 하나의 값에 매핑될 수 있다.

각 객체의 주소값을 저장하고 있으며, value는 중복 가능하다.