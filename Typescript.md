

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

```typescript

interface MyComplexInterface<Event, Context, Name, Point> {

getEvent: () => Event;

getContext: () => Context;

getName: () => Name;

getPoint: () => Point;

}

  

type Example = MyComplexInterface<

"click",

"window",

"my-event",

{ x: 12; y: 14 }

>;

  

type GetPoint<T> = T extends MyComplexInterface<any, any, any, infer TPoint> ? TPoint : never;

  

type tests = [Expect<Equal<GetPoint<Example>, { x: 12; y: 14 }>>];

```
