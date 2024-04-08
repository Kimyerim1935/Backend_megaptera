## ✔️ 키워드 정리

### 관심사의 분리

### 응집도

### 결합도

### Layered Atchitecture

### UUID

```java
package com.yerm.api.rest.demo.controllers;

import com.yerm.api.rest.demo.application.PostService;
import com.yerm.api.rest.demo.dtos.PostDto;
import com.yerm.api.rest.demo.exceptions.PostNotFound;
import org.springframework.http.HttpStatus;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PatchMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseStatus;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;

@RestController
@RequestMapping("/posts")
public class PostController {
   private PostService postService;

   public PostController() {
       PostService postService = new PostService();

   }

   @GetMapping
   public List<PostDto> list(
   ) {
       List<PostDto> postDtos = postService.getPostDtos();
       return postDtos;
   }

   @GetMapping("/{id}")
   public PostDto detail(@PathVariable("id") String id) {
       PostDto postDto = (PostDto) postService.getPostDto(id);

       return postDto;
   }


   @PostMapping
   @ResponseStatus(HttpStatus.CREATED)
   public PostDto create(@RequestBody PostDto postDto) {
//        String id = UUID.randomUUID().toString().replace("-", "");
//        String id = UlidCreator.getUlid().toString();
       PostDto created = postService.createPost(postDto);

       return created;
   }

   @PatchMapping("/{id}")
   public PostDto update(@PathVariable String id,
                         @RequestBody PostDto postDto) {
       PostDto updated = postService.updatePost(id, postDto);

       return updated;
   }

   @DeleteMapping("/{id}")
   public PostDto delete(@PathVariable String id) {
       PostDto postDto = postService.deletePost(id);

       return postDto;
   }


   @ExceptionHandler(PostNotFound.class)
   @ResponseStatus(HttpStatus.NOT_FOUND)
   public String postNotFound() {
       return "게시물을 찾을 수 없습니다. \n";
   }
}
```
