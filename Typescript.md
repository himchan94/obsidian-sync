

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

```typescript

const getServerSideProps = async () => {

const data = await fetch("https://jsonplaceholder.typicode.com/todos/1");

const json: { title: string } = await data.json();

return {
	props: {
		json,
			},
	   };
};

  
  
  
  

type InferPropsFromServerSideFunction<T> = T extends () => Promise<{props: infer TData}> ? TData : never;

  

type tests = [

Expect<Equal<InferPropsFromServerSideFunction<typeof getServerSideProps>,
{ json: { title: string }}>>
];


```
