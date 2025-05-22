

### 1. type spcae, value space


### infer using with extends
```typescript


type GetDataValue<T> = T extends {data : infer T2} ? T2 : never;

  

type tests = [

Expect<Equal<GetDataValue<{ data: "hello" }>, "hello">>,

Expect<Equal<GetDataValue<{ data: { name: "hello" } }>, { name: "hello" }>>,

Expect<

Equal<

GetDataValue<{ data: { name: "hello"; age: 20 } }>,

{ name: "hello"; age: 20 }

>

>,

// Expect that if you pass in string, it

// should return never

Expect<Equal<GetDataValue<string>, never>>,

];

```
