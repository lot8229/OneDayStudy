# Bytes 와 Str 의 차이를 알아두자.

- 시퀀스 란? 
  - 문자열 , 수열 등 특정 데이터가 열거되어있는 자료형을 **시퀀스** 라고 한다.

- 파이썬의 문자열 시퀀스에는 **Bytes** 타입 과 **Str** 타입이 있다.
  - ### Byte

    Byte 문자열에는 부호가 없는 8바이트 데이터가 그대로 들어간다. 
    
    ```python
        a = b'h\x65llo'
        print (list(a))
        print (a)

        >>>
        [104,101,108,108,111]
        b'hello'
    ```
  - ### Str

    str 인스턴스에는 사람이 사용하는 언어의 문자를 표현하는 유니코드 codPoint 가 들어있다.

    ```python
        a = 'a\u0300 propos'
        print (a)
        >>>
        à propos
    ```

    > **!** 중요한점
    - 여기서 str 과 bytes 서로 대응하는 인코딩이 없다
        
        때문에 str 에서 bytes 로 변환 할때 
        `str 의 encode 메소드` 를 호출해야하고

        bytes 에서 str 로 변환할때 `bytes 의 decode 메소드` 를 호출해야한다.


        그래서 내가 원하는 방식으로 인코딩 방식을 명시적으로 지정 할수 도 있고 
        시스템 디폴트 인코딩을 받아들일수도 있다.
        (일반적으로는 UTF-8 이 시스템 디폴트 인코딩 이지만 항상 UTF-8 이 디폴트 인것은 아니다.)

  - ### Encode & Decode
    - 파이썬 프로그램 을 작성할 때 유니코드 데이터를 인코딩 하거나 디코딩 하는 부분을 인터페이스의 가장 먼 경계 부분에 위치시켜라.
    - 유니코드 데이터가 들어있는 str 을 사용해야하며 , 어떠한 가정도 하면 안된다.
    - 이런 접근 방식을 사용하게 된다면 다양한 텍스트 인코딩을 input 받을수 있고, 출력 테스트 인코딩은 한가지로 제한될 수 있다.

    - 문자를 표현하는 타입이 둘로 나눠져 있기 때문에 파이썬 코드를 작성할때 두가지 상황이 자주 발생한다.
      - UTF-8(예시) 로 인코딩된 8비트 시퀀스를 그대로 사용하고 싶다.
      - 특정 인코딩을 지정하지 않은 유니코드 문자열을 사용하고 싶다.

    두가지 상황중 일치하는 값을 확신하기 위해 도우미 함수가 필요할때가 있다.
    ```python
    def to_str(bytes_or_str):
      if isinstance(bytes_or_str,bytes):
        value = bytes_or_str.decode('utf-8')
      else:
        value = bytes_or_str
      return value # str 인스턴스

    print(repr(to_str(b'foo')))
    print(repr(to_str('bar')))
    print(repr(to_str(b'\xed\x95\x9c')))

    >>>
    'foo'
    'bar'
    '한'
    ```
    > **!** 꼭 기억해야할 문제점
    - bytes 와 str 은 같은 타입끼리는 비교나 연산이 되지만, 서로 다르면 비교,연산 이 되지 않는다.
    - 마찬가지로 형식화 문자열 (%) 도 같은 타입끼리만 된다.
    - 파일 핸들링 관련 연산들이 디폴트로 유니코드 문자열을 요구하고 이진바이트 문자열은 요구하지 않는것
      - 이는 파일을 열때 w, r 등이 아닌 wb , rb 등 이진 모드를 통해 파일을 열면 해결된다.
      - open 함수의 encoding 파라미터를 명시하면 플랫폼에 따라 동작이 달라질 일이 없어진다. 