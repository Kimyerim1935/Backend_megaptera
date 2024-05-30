## ✔️ 키워드 정리

### Multipart FormData

[Multipart FormData](https://dev.to/aurelmegn/multipartformdata-why-is-it-recommended-461n)는 클라이언트에서 서버로 `form data`를 전송하는 방법이다.

HTTP POST 요청으로 다양한 유형의 데이터를 보내는 데 필수적이다.

이런식으로 사용하면 된다.

```html
<form
	action="http://localhost:8080/images"
	method="POST"
	enctype="multipart/form-data">
	<p>
		<label for="input-file">File:</label>
		<input id="input-file" type="file" name="image" />
	</p>
	<p>
		<button type="submit">Submit</button>
	</p>
</form>
```

### @ModelAttribute

`@ModelAttribute`는 Model의 attribute에 접근하는 메서드이다.

메서드의 반환값이나 메서드의 파라미터의 값으로 동일한 이름을 가지는 모델 attribute의 값을 업데이트한다.

이런식으로 사용하면 된다.

```java
@RestController
@RequestMapping("images")
public class ImageController {
    @PostMapping(consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
    @ResponseStatus(HttpStatus.CREATED)
    public String create(
            @ModelAttribute UploadImageDto imageDto
    ) {
        MultipartFile multipartFile = imageDto.image();

        if (multipartFile == null || multipartFile.isEmpty()) {
            return "No image";
        }

        return multipartFile.getOriginalFilename();
    }
}
```

✨ Reference

https://varaprasadh.medium.com/what-the-heck-is-multipart-form-data-8df091d598b5<br/>
https://developer.mozilla.org/en-US/docs/Web/API/FormData
