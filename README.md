# Josa

Josa는 선행명사의 형태에 따라 적절한 조사를 찾아줍니다.

## 설치

```shell
npm install josa
```

## 사용법

Josa는 기본적으로 주 함수 하나만을 노출하고 있습니다. 이 함수는 입력받은 문자열에 포함된 플레이스홀더를 적절한 조사로 대체합니다.

``` javascript
import josa from 'josa'

josa('친구#{이} 선생님#{와} 함께 학교#{으로} 간다.')
// => '친구가 선생님과 함께 학교로 간다.'

const book = getBookFromSomewhere()

josa(`${book.title}#{는} ${book.author}#{이} 쓴 책이고, ISBN은 ${book.isbn}#{예요}.`)
// => '자연의 이야기들은 쥘 르나르가 썼고, ISBN은 xxxxxxxxxxxx3이에요.'

josa('숫자#{이} 3#{가} 되었다.')
// => '숫자가 3이 되었다.'

josa('값#{가} 7#{으로} 바뀐다.')
// => '값이 7로 바뀐다.'
```

## 특징

- 플레이스홀더 앞의 명사에 따라 두 개의 조사 형태 중 하나가 선택됩니다. 예를 들어 `#{커피}는`이나 `커피#{은}`을 `커피는`으로 바꿉니다.

- 선행명사가 한글이나 숫자로 끝나는 경우를 지원합니다.

- 플레이스홀더는 해시(`#`) 기호가 붙은 중괄호로 표기하며, 선행명사와 플레이스홀더 사이에 공백이 없어야 합니다.

- 플레이스홀더 앞에 소괄호(`(`, `)`)로 묶인 글이 올 때 조사의 형태는 괄호 앞의 단어에 따릅니다.
``` javascript
josa('둘리(아기 공룡)#{은}')
// => '둘리(아기 공룡)는'
```

- 플레이스홀더의 종류는 다음과 같습니다.


| 조사 | 플레이스홀더 | 예시 |
|:-:|:-:|:-:|
| 은/는 | `#{은}` / `#{는}` | `길동#{는}` => `길동은` |
| 이/가 | `#{이}` / `#{가}` | `길동#{가}` => `길동이` |
| 을/를 | `#{을}` / `#{를}` | `길동#{를}` => `길동을` |
| 과/와 | `#{과}` / `#{와}` | `길동#{와}` => `길동과` |
| 이랑/랑 | `#{이랑}` / `#{랑}` | `길동#{랑}` => `길동이랑` |
| 이나/나 | `#{이나}` / `#{나}` | `길동#{나}` => `길동이나` |
| 이라서/라서 | `#{이라서}` / `#{라서}` | `길동#{라서}` => `길동이라서`|
| 으로/로 | `#{으로}` / `#{로}` | `길동#{로}` => `길동이로` |
| 이에요/예요 | `#{이에요}` / `#{예요}` | `길동#{예요}` => `길동이에요` |
| 이라고/라고 | `#{이라고}` / `#{라고}` | `길동#{라고}` => `길동이라고` |
| 아/야 | `#{아}` / `#{야}` | `길동#{야}` => `길동아` |

## 테스트

```shell
npm install

npm test
```