1. poetry를 사용하여 가상환경을 구축하고 Poetry 에서 제공하는 Dependencies를 옵션을 활용할 줄 안다.
2. FastAPI 프로젝트를 구성하여 서버를 실행할 줄 안다.
3. ruff, black, isort 등의 코드 포매터 라이브러리를 이해하고 있다.
4. mypy 라이브러리의 개념에 대해서 이해하고 활용할 줄 안다.
5. pytest 를 이해하고 이를 이용하여 파이썬 코드 테스트를 진행하기 위한 세팅을 할 수 있다.

오늘 배운 내용(0929): 1, 3, 4에 해당?

- `poetry` 사용 가상환경 및 `dependencies`: 스크린샷으로 대체<br>
- `ruff` , `black` , `isort` : 라이브러리 설치 완료.<br>
- `mypy`: 라이브러리 설치 완료. 하단 트러블슈팅 해결 <br>

> print()가 미처 삭제되지 않은 게 있는지 확인하는 습관 가지기<br>
> why? print는 비싼 연산.<br>
> 이건 IO라서(input, output)은 외부와 소통하는 것이라 리소스 많이 잡아먹어요.

>MyPy가 아주 중요합니다! 효자다. 하이 노력, 하이 리턴이다.
  
#### 정적 타입 체킹 mypy, strict를 배우면서 타입 친화적으로 개발하는 방법을 배운다.
static과 dynamic의 차이가 뭐죠?
> static: 실행하기전에 이미 결정된 것
> dynamic: 실행중에 바뀌는 것 or 실행중에 결정되는 것
> <br>리터럴: 그냥 값입니다.(1,33, 55.1 "유추" True False)
> <br>마이파이의 인퍼런스: 힌트가 없을 때 유추하는 것. 

```python
def type_print_desu(nominate):
    a= type(nominate)
    print(a)
    
my_str: str = "abc"
my_list: list[str] = ["abc", "def"]
type_print_desu(my_list)
# 추론이 가능할 경우는 안 적어줘도 되긴 함
my_list = ["abc", "def"]
type_print_desu(my_list)
# 파이프라인

or_type_list: list[str | int] = ["a", 3]
type_print_desu(or_type_list)
or_type_list: list[str | bool] = ["abc", 0]
type_print_desu(or_type_list)
# bool은 int가 맞지만 int는 bool이 아니기 때문에, 0이나 1 과 다른 정수를 넣으면 오류 발생하겠죠?
```

<details>
    <summary>트러블 슈팅 내역
    </summary>
    <details>
            <summary>1. `POETRY` 경로 못 찾는 오류 </summary>
                하...poetry랑 black이랑 해결하는데 2시간은 썼다.<br>PYTHON 폴더 내에서 POETRY를 찾지 못하는 issue.
                <br>해결방법은 gpt를 써서 전역에서 설치.<br><br>다음 코드를 실행함:
            <ul>
                <li>py -3.13 -m pip install --user pipx</li>
                <li>py -3.13 -m pipx ensurepath</li>
                <li>새 터미널 열기</li>
                <li>pipx install poetry</li>
                <li>poetry --version</li>
            </ul>
    </details>
    <details>
            <summary> 2. FASTAPI 라이브러리 오류
            </summary>
             <br>현재 트러블: error: Cannot find implementation or library stub for module named "fastapi"  [import-not-found]
             <br>해결법은 fastapi 라이브러리를 다운받는 명령어를 CMD (윈도우 쉘에서 누르면 들어갈 수 있다.<br> 들어가자마자 나오는 거 아님) 에서 실행하는 것.
             <ul>
                <li>pip install fastapi[standard]</li>
                <li>라이브러리 설치 후 오류 더 이상 발생하지 않음.</li>
             </ul>
    </details>
</details>