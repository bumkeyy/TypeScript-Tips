# `generic` 사용하는 여러가지 방법

[원문](https://twitter.com/mpocock1/status/1508757718630342657?s=20&t=R0ASuxvbXG_wUb6amQ6crw)

  - [1. 함수](#1-함수)
  - [2. 유명 화살표 함수](#2-유명-화살표-함수)
  - [3. 익명 화살표 함수](#3-익명-화살표-함수)
  - [4. 클래스](#4-클래스)
  - [5. 타입과 인터페이스](#5-타입과-인터페이스)
  - [6. 객체 타입 내부에서 선언된 함수](#6-객체-타입-내부에서-선언된-함수)
  - [7. `infer` 키워드](#7-infer-키워드)

## 1. 함수

함수 선언시에 `generic` 슬롯을 추가할 수 있습니다. `()` 앞에 위치하며 보통 input의 타입으로 사용됩니다.

다음 예제는 `input`으로 들어온 타입과 동일한 타입을 반환하는 `myFunction` 함수입니다.

```ts
function myFunction<TType>(t: TType): TType {
  return t;
}

const num = myFunction(20);
//    ^ const num: 20
```

[플레이그라운드 예제](https://www.typescriptlang.org/play?#code/GYVwdgxgLglg9mABAWwJ4DFzXmAPAFX1QAcBTAPgAooAuRQk0gShobMQG8AoRRAJ1JQQfJFADcXAL5cuEBAGcoiMCGSIAvCgxZYCSgCYADEy4B6U70QA9APxA)

## 2. 유명 화살표 함수

화살표 함수에도 동일한 구문을 적용할 수 있습니다.

```ts
const myArrowFunction = <TType>(t: TType): TType => {
  return t;
};

const str = myArrowFunction('some string');
//    ^ const str: "some string"
```

> :warning: `tsx`파일에서 화살표 함수에서는 `<>`를 JSX 태그로 잘못 인식하여 `<TType, >` 혹은 `<TType extends {}>` 를 사용합니다.

[플레이그라운드 예제](https://www.typescriptlang.org/play?#code/MYewdgzgLgBAtgTwIICcUgO4DECuZhQCW4MAvDADwAqVCADgKYA0AfABRQBcMN9DAlJ16MyLGAG8AUDBgoGUHCjAwokgL6TJoSLGgoy8ZGky58RcGwDkEEHAYw9hMAHNL-SQHoPMmQD0A-EA)

## 3. 익명 화살표 함수

함수를 리턴하는 익명의 함수나 화살표 함수에서도 `generic`을 사용할 수 있습니다.

`generic` 함수인 `func`를 `curriedFunctionCreator`로 부터 만들 수 있습니다.

```ts
const curriedFunctionCreator =
  () =>
  <TType>(t: TType): TType => {
    return t;
  };

const func = curriedFunctionCreator();
//     ^ const func: <TType>(t: TType) => TType

const str = func('some string');
//     ^ const str: "some string"
```

## 4. 클래스

생성자에서 인자의 타입을 추론하기 위해 `generic`을 사용할 수 있습니다.

다음 예제는 생성자로 전달받은 인자의 타입을 이용해서 클래스 내부에서 동적인 타입을 만들 수 있습니다.

```ts
class MyClass<MapMember> {
  constructor(public map: Record<string, MapMember>) {}
}

const mapClass = new MyClass({ a: 1, b: 2 });

const map = mapClass.map;
//    ^ const map: Record<string, number>
```

[플레이그라운드 예제](https://www.typescriptlang.org/play?#code/MYGwhgzhAECyCeBhcUA8swAdYFMC2ARjgE4B80A3gFDTTAD2AdhAC7ECuwL9xAFJuwIgAlsGh4sALgBKOBsQAmqVsWGMA5gBo4WXIRKkAlJQC+VM1QbMW4rMkgwAvNEY4A7nCQoIvCmEnQAIzaBAEATCaGVJZMrLaY0M4SmPZQAHTJVAD0WbS0AHoA-EA)

## 5. 타입과 인터페이스

타입 / 인터페이스를 재사용하거나 동적으로 사용해야 할 때 `generic`을 사용할 수 있습니다.

다음 코드는 동적으로 전달 받은 타입으로 record를 만드는 `MyType`과 `T`를 받아서 `{value: T}`를 만드는 `ValueContainer` 입니다.

```ts
type MyType<T> = Record<string, T>;

type RecordOfNumbers = MyType<number>;
//   ^ type RecordOfNumbers = { [x: string]: number; }

interface ValueContainer<T> {
  value: T;
}

type StringContainer = ValueContainer<string>;
//   ^ type StringContainer = ValueContainer<string>
```

[플레이그라운드 예제](https://www.typescriptlang.org/play?#code/C4TwDgpgBAsiAq4IB54D4pQLxQEoQGMB7AJwBNkBnYEgSwDsBzAGinQCh3RI9DSyA8gDMAcgFcAtgCMIJStlgIkyepJkk07APRbMUAHoB+Tg2CyhAQwLQAahYA2YiAGEi9YBYazUGAN7tMADcHJwAuNnYAX05uaABlGgZGV3dPelkFO0cXNw8vEipEpk0dPSN2IA)

## 6. 객체 타입 내부에서 선언된 함수

타입 / 인터페이스 / 객체 선언 내부에 인라인으로 `generic`을 사용할 수 있습니다.

다음 코드는 `obj.myFunc` 에 `generic`을 사용했습니다.

```ts
type Obj = {
  myFunc: <TType>(t: TType) => TType;
};

const obj: Obj = {
  myFunc: (t) => t,
  //^ (property) myFunc: <TType>(t: TType) => TType
};

const str = obj.myFunc('some thing');
//    ^ const str: "some thing"
```

[플레이그라운드 예제](https://www.typescriptlang.org/play?#code/C4TwDgpgBA8gRgKygXigbwFBSgWxAMQFcA7AYygC4oAeAFVvAgD4AKYC+xgShSak8gYAvhgykA9sQDOwKOMQV4SVJmx4iZKmx7ImwDAHoDAPQD8w0ROmyZAJxRzEAOnUlSLAORTxOaMAAWAJbEAOYeXIYG2NhmQA)

## 7. `infer` 키워드

조건부 타입 검사내에서 `infer` 키워드를 사용해서 조건에 따라 `generic`을 추론할 수 있습니다.

확인하려는 타입 / 인터페이스에서 직접 `generic`을 가져올 때 유용합니다.

```ts
interface ValueContainer<TValue> {
  value: TValue;
}

type GetContainerValue<TContainer> = TContainer extends ValueContainer<
  infer TValue
>
  ? TValue
  : never;

const container = {
  value: 'some string',
};

type ContainerValue = GetContainerValue<typeof container>;
//   ^ type ContainerValue = string
```

[플레이그라운드 예제](https://www.typescriptlang.org/play?#code/JYOwLgpgTgZghgYwgAgGpwDYFcIGED24co0APACrrYQB8yA3gFDLIBumOAXMpRxIwF9GjMAE8ADigDiEMASIkoVHBXlhiIaHQC8PNRujIIAD0ggAJgGc0ffYtKgYh3tToB+HspTdNraAG5hBEJLMGRghU0oZF0mFnZqbgByS3wAWxRQqFAAcyTBYTFJZDsorxjkGTlCdUUvUiKIfBhwmoMoGkYAei6WZAA9NyA)
