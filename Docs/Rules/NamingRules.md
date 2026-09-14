# 코드 이름 규칙

C# 스크립트를 만들거나 고칠 때 따르는 규칙입니다. 규칙은 이 문서에만 적습니다.

## 이름 짓기

| 대상 | 형식 | 예시 |
|---|---|---|
| 클래스 | PascalCase | `PlayerMovement` |
| 메서드 | PascalCase | `CollectItem()` |
| 프로퍼티 | PascalCase | `Score` |
| private 필드 | `_` + camelCase | `_moveSpeed` |
| 지역 변수·매개변수 | camelCase | `itemCount` |
| 상수 | ALL_CAPS | `MAX_HEALTH` |
| enum 타입·값 | PascalCase | `GameState.Playing` |

## 파일

- 파일 하나에 클래스 하나를 둡니다.
- 파일 이름과 클래스 이름을 똑같이 짓습니다. 다르면 유니티가 클래스를 잘못 고르거나 컴포넌트로 쓰지 못하는 경우가 생깁니다.
- 이름에 공백과 한글을 쓰지 않습니다.

## 인스펙터에 보이는 값

- 인스펙터에서 조절할 값은 `public` 필드 대신 `[SerializeField] private` 필드로 둡니다.

```csharp
public class PlayerMovement : MonoBehaviour
{
    [SerializeField] private float _moveSpeed = 5f;
}
```

## 컴포넌트 가져오기

- `GetComponent`는 `Update`에서 매 프레임 부르지 않습니다. `Awake`에서 한 번 가져와 필드에 담아 둡니다.

```csharp
private Rigidbody2D _rigidbody;

private void Awake()
{
    _rigidbody = GetComponent<Rigidbody2D>();
}
```

## 로그

- `Debug.Log` 메시지 앞에 클래스 이름을 붙입니다. 콘솔에서 어느 스크립트가 남긴 로그인지 바로 찾기 위해서입니다.

```csharp
Debug.Log($"PlayerMovement: 아이템 획득 {itemCount}개");
```
