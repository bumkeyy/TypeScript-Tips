# TypeScript-Tips

TypeScript Tips for Koreans

## This repo

타입스크립트 사용에 관한 팁에 대해 정리하는 레포입니다.
대부분 한글로 번역하거나 경험에 의해서 정리된 내용이기 때문에 오역 및 잘못된 정보가 있으면 언제든 PR 날려주세요! :smile:

### [TypeScript Tip - Matt Pocock(twitter)](https://twitter.com/mpocock1)

[Matt Pocock](https://twitter.com/mpocock1)님이 트위터에서 정리해 준 내용을 바탕으로 번역 및 작성되었습니다.

> [`generic` 사용하는 여러가지 방법](./docs/twitter/matt-pocock/generic_example.md) / [twitter](https://twitter.com/mpocock1/status/1508757718630342657?s=20&t=HnztxY7c5D32iY_-WaN6-w)

1. [객체에서 유니언 타입 추출하기](./docs/twitter/matt-pocock/1.how_to_derive_a_union_type_from_an_object.md) / [twitter](https://twitter.com/mpocock1/status/1497262298368409605)
2. [`in` 연산자를 사용해서 유니언 타입 수정하기](./docs/twitter/matt-pocock/2.transform_a_union_to_another_union_using_in.md) / [twitter](https://twitter.com/mpocock1/status/1498284926621396992?s=20&t=oez-3xavZMDYePJp5sVHEw)
3. [문자열 보간을 통해 타입 레벨에서 쿼리스트링 타입 추출하기](./docs/twitter/matt-pocock/3.decode_URL_search_params_using_string_interpolation.md) / [twitter](https://twitter.com/mpocock1/status/1499002040168636420?s=20&t=5k4HgmoEfoRrIio-TeoUag)
4. [함수 오버로딩과 제네릭을 이용해서 `compose` 함수 타입 선언하기](./docs/twitter/matt-pocock/4.Function_overloads_with_%20generics.md) / [twitter](https://twitter.com/mpocock1/status/1499730377337827336?s=20&t=CRwo0bNh33vEkVnUSNVcIA)
5. [`extends`를 활용해서 내부 요소 타입을 추론 및 자동 완성하기](./docs/twitter/matt-pocock/5.narrow_the_value_of_a_generic_to_enable_autocomplete_and_inference_using_extends.md) / [twitter](https://twitter.com/mpocock1/status/1500813765973053440?s=20&t=c8SpcS-HPqJWBjoWjggkTA)
6. [`infer`를 이용해서 리액트 컴포넌트의 `Props` 타입 추론하기](./docs/twitter/matt-pocock/6.extract_props_from_react_component_using_infer.md) / [twitter](https://twitter.com/mpocock1/status/1501533441791193090?s=20&t=fDvb9ToAIUY1UGT2q2r8pA)
7. [`generic`과 `keyof`을 사용해서 type-safe한 `Object.keys` 구현하기](./docs/twitter/matt-pocock/7.object_keys_using_generic_and_keyof.md) / [twitter](https://twitter.com/mpocock1/status/1502264005251018754?s=20&t=3SbKlwJvdPEkX2bveWrZ1A)
8. [리액트 컴포넌트에서 제네릭 사용하기](./docs/twitter/matt-pocock/8.generic_in_react.md) / [twitter](https://twitter.com/mpocock1/status/1503352924537339904?s=20&t=GswnqXu4Fg7f-IK4WOZtAA)
9. [`generic`을 사용해서 `key remover` 함수 구현하기 (w/ `curried`)](./docs/twitter/matt-pocock/9.generic_in_key_remover.md) / [twitter](https://twitter.com/mpocock1/status/1504088070869884929?s=20&t=ZUtnL5S9W0eueCBBkl-CzA)
10. [함수의 런타임 체크를 타입 레벨에서 검사하기](./docs/twitter/matt-pocock/10.check_type_level.md) / [twitter](https://twitter.com/mpocock1/status/1504802045794078723?s=20&t=ujhYUKWxMf3a2i7mx4h0lw)
11. [`DeepPartial` 구현하기](./docs/twitter/matt-pocock/11.deep_partials.md) / [twitter](https://twitter.com/mpocock1/status/1505892984658743300?s=20&t=JLIlaCLOi3UZWHOAo3hLZA)
12. [`LooseAutoComplete` 구현하기](./docs/twitter/matt-pocock/12.LooseAutocomplete.md) / [twitter](https://twitter.com/mpocock1/status/1506607945445949446?s=20&t=YYaQriqq48F_A4WMNX72LQ)
13. [`typeof`를 이용해서 모듈을 타입으로 가져오기](./docs/twitter/matt-pocock/13.type_module_using_typeof.md) / [twitter](https://twitter.com/mpocock1/status/1508408811635322883?s=20&t=jVoPfKOCP7khv9C6hIhtewhttps://twitter.com/mpocock1/status/1508408811635322883?s=20&t=jVoPfKOCP7khv9C6hIhtew)
14. [`declare`를 이용해서 global 타입을 선언하기](./docs/twitter/matt-pocock/14.declare_global.md) / [twitter](https://twitter.com/mpocock1/status/1509131700382715905?s=20&t=eHwePGAOfhlUG2xEq6vyZw)
15. [`generic`을 이용해서 동적으로 타입을 구체화하기](./docs/twitter/matt-pocock/15.using_generic_dynamic.md) / [twitter](https://twitter.com/mpocock1/status/1509850662795989005?s=20&t=toAEeTeDUW0sIdckAPkcJQ)


### [Type Challenge](https://github.com/type-challenges/type-challenges)

타입을 연습할 수 있는 레포입니다! :rocket::fire:

## Other Repos related TypeScript

- [utility-types](https://github.com/piotrwitek/utility-types)
- [ts-toolbelt](https://github.com/millsp/ts-toolbelt)
- [type-fest](https://github.com/sindresorhus/type-fest)
- [$mol_type](https://github.com/hyoo-ru/mam_mol/tree/master/type)
