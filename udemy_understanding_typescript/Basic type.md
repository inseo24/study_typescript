# Understanding TypeScript

### CH02: TypeScript Basic & Basic Types

- 타입스크립트에서 primitive type들은 전부 lowercase 사용
    - string, number
- type inference(타입 추론)
    - 그래도 타입을 명시해주는게 좋은듯!
- JS와 TS 타입의 차이점
    - TS 타입은 컴파일 시점에 체크되고, JS 타입은 런타임에 체크
- object in TS
    
    ```tsx
    const person: {
    	name: string;
    	age: number;
    } = {
    	name: 'seoin',
    	age: 27
    };
    
    console.log(person.name);
    // compile 되기 전에는 
    // name, age 타입을 명시하지 않으면 에러가 뜸
    
    // compile 된 후에
    // 명시된 타입을 지워도 에러가 뜨지 않음
    ```
    
- Nested Objects & Types
    
    ```tsx
    const product: {
      id: string;
      price: number;
      tags: string[];
      details: {
        title: string;
        description: string;
    	}
    } = {
      id: 'abc1',
      price: 12.99,
      tags: ['great-offer', 'hot-and-new'],
      details: {
        title: 'Red Carpet',
        description: 'A great carpet - almost brand-new!'
      }
    }
    ```
    
- Arrays Types
    - any[], string[], number[] (…)
- Tuples - fixed-length array
    
    ```tsx
    const peron: {
    	role: [number, string];
    } = {
    	role: [2, 'author']
    };
    
    ```
    
- Enums
    
    ```tsx
    enum Role { ADMIN = 'ADMIN', READ_ONLY = 5, AUTHOR };
    ```
    
- any
- Union Types
    
    ```tsx
    function combile(input1: number | string, input2: number | string) {
    	const result = input1 + input2;
    	return result;
    }
    
    const combinedAges = combine(30, 26);
    console.log(combinedAges);
    
    const combinedNames = combine('Max', 'Anna');
    ```
    
- Literal Types
- Type Alias / Custom Types
    
    ```tsx
    type Combinable = number | string;
    type ConversionDescriptor = ‘as-number’ | ‘as-text’;
    
    type User = { name: string; age: number };
    const user1: User = { name: 'Max', age: 30 };
    
    function greet(user: { name: string; age: number }) {
    	console.log('Hi, I am ' + user.name);
    }
    ```
    
- Function Return Types & “void”
    
    ```tsx
    function add(n1: number, n2: number): number {
    	return n1 + n2;
    }
    
    function printResult(n1: number, n2: number): void {
    	console.log(n1 + n2);
    }
    ```
    
- Function as Types
    
    ```tsx
    function add(n1: number, n2: number) {
    	return n1 + n2;
    }
    
    let combineValues: Function;
    combineValues = add;
    
    console.log(combineValues(8, 8));
    
    ------------------------
    
    let combineValues: (a: number, b: number) => number;
    ```
    
- Function Types & Callbacks
    
    ```tsx
    function addAndHandle(n1: number, n2: number2, cb: (num: number) => void): never {
    	const result = n1 + n2;
    	cb(result);	
    }
    
    addAndHandle(10, 20, (result) => {
    	console.log(result);
    });
    ```
    
- “unknown” Type
    
    ```tsx
    let userInput: unknown;
    let userName: string
    
    userInput = 5; // ok
    userInput = 'Max'; // ok
    
    if (typeof userInput === 'string') {
    	userName = userInput; 
    }
    ```
    
- “never” Type
    
    ```tsx
    function generateError(message: string, code: number) {
    	throw {message: message, errorCode: code};
    }
    // never -> 오류 or return 없음
    
    const result = generateError('An error occured!', 500)
    console.log(result);
    ```
    

