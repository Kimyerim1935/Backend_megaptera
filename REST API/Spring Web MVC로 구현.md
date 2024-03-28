## ✔️ 키워드 정리

### @RequestMapping

요청이 들어온 URI의 요청과 Annotation value 값이 일치하면 해당 클래스나 메서드가 실행된다.
Controller 객체 안의 메서드와 클래스에 적용 가능하다.

### @GetMapping

RequestMapping(Method=RequestMethod.GET)과 똑같은 역할을 한다.

### @PostMapping

RequestMapping(Method=RequestMethod.POST)과 똑같은 역할을 한다.

### @PatchMapping

기존의 정보를 수정할 때 주로 사용한다.

### @DeleteMapping

기존의 정보를 삭제할 때 사용한다.

### @PathVariable

요청 URI 매핑에서 템플릿 변수를 처리하고 메서드 매개변수로 설정할 수 있다.

### @RequestBody

Body에 전달되는 데이터를 머서드의 파라미터와 매칭시켜 데이터를 받아 처리할 수 있는 Annotation이다. 클라이언트가 보내는 HTTP요청(JSON 및 XML)을 Java Object로 변환한다.

### @ExceptionHandler

Controller 계층에서 발생하는 에러를 잡아서 메서드로 처리해주는 기눙이다. Service, Repository에서 발생하는 에러는 제외한다. 

### @ResponseStatus

