

```js

<script>

let l0 = 'l0';

function fn2() {
	let l2 = 'l2';
	console.log(l0, l1, l2);
}

function fn1() {
	let l1 = 'l1';
	console.log(l0, l1);
	fn2();
}

fn1();
</script>


```

```js

<script>
let l0 = 'l0';


function fn1() {

	function fn2() {
		let l2 = 'l2';
		console.log(l0, l1, l2);
	}

	let l1 = 'l1';
	console.log(l0, l1);
	fn2();
}

fn1();
</script>
```


```js


<script>
let l0 = 'l0';


function fn1() {

	function fn2() {
		function fn3() {
			let l3 = 'l3';
			console.log(l0, l1, l2, l3);
		}
		
		let l2 = 'l2';
		console.log(l0, l1, l2);
		fn3();
	}

	let l1 = 'l1';
	console.log(l0, l1);
	fn2();
}

fn1();
</script>


```

![[Pasted image 20241012140242.png]]


dynamic scope 와 static scope(lexical scope)