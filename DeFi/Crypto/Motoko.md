# Motoko

## Links 

- [Base index](https://github.com/dfinity/motoko/blob/master/doc/md/base/index.md)

## Questions

- [ ] What the heck is NNS and how it work
- [ ] How does ICP swork in gerneral
- [ ] Good template for Motoko Vessel project.
- [ ]  Question on dhall. 
	- How to correctly  reference on GitHub

- [ ] Order (how to use how to crate) 
    - Lyamda methods.

- [ ]  Unit testing ?
    - how to correctly right unitt test
    - Sutites,Matchers, Testables? 
- [ ] Async/Await testing

- [ ] Iter ( toChar)?

- [ ] Array freezing/unfizing usage of buffers.
	
## Modules 

Are files basically

```motoko
import Counter "../src/Counter";
import Counter "Counter";
import Result "mo:base/Counter";
import {map,find,field, fold = fold} "mo:base/Array";


module some{}
module {}

```
## Folder Structure

```motoko

root
|
--src
|
--test
|
--example

```

## Vessel

[Github repo](https://github.com/dfinity/vessel)

`$(vessel bin)/moc $(vessel sources) -wasi-system-api main.mo`

For motoko non-dfx projects.
`$(vessel bin)/moc` - command to start working with a prject or something

**Vessel** - Is a package manager for motoko specificely

`vessel init`

`$bin\vessel --version` or `vessel --version`

**Dhall**-  is a programmable configuration language that you can think of as: JSON + functions + types + imports

`vessel.dhall`

```dhall
{
	dependencies = [ "base" ], 
	compiler = Some "0.6.2" 
}

```

`package-set.dhall`

```dhall
let upstream = https://github.com/dfinity/vessel-package-set/releases/download/mo-0.6.21-20220215/package-set.dhall sha256:b46f30e811fe5085741be01e126629c2a55d4c3d6ebf49408fb3b4a98e37589b
let Package =
    { name : Text, version : Text, repo : Text, dependencies : List Text }

let
  -- This is where you can add your own packages to the package-set
  additions =
    [] : List Package

let
  {- This is where you can override existing packages in the package-set

     For example, if you wanted to use version `v2.0.0` of the foo library:
     let overrides = [
         { name = "foo"
         , version = "v2.0.0"
         , repo = "https://github.com/bar/foo"
         , dependencies = [] : List Text
         }
     ]
  -}
  overrides =
    [] : List Package

in  upstream # additions # overrides
```

#### Run vessel check

`$(vessel bin)/moc $(vessel sources) --check` - check our files


`$(vessel bin)/moc -r test/zeroTest.mo` - check our files


### Import package 

To import pckage we need :

1. In `package-set.dhall` define package `array` and github link
2. In `main.mo` define `import mo:arra/Array`

 

## Field visability    	

- `private` - enclosing object 
- `public` 
- `system` - actor field


## Unit testing

 [Motoko color repo](https://github.com/ByronBecker/motoko-color) Repo with unit tests setup to start making the unit test on local machine
`make test` - to run the unit tests in that repo

### Lyamda Fucnctions

```
```

## Variable declation 

if u declare variable through the `let` you would not be able to latter change it or use incide of the loop

### Let Declaration

`let <pat> = <exp>`
- `<exp>` has type `T`
- `<pat>` has type `T`

`let` is *immutable*

```motoko


```

### Var Declation

**VAR** is *mutable* declaration `var <id> (: <typ>)? = <exp>`

- If the annotation `(:<typ>)?` is present, then `T == <typ>`.
    	
## Type decalartion

`  type Person = { first : Text; last : Text };`

The declaration type `<id> <typ-params>? = <typ>` declares a new type constructor `<id>`, with optional type parameters `<typ-params>` and definition `<typ>`.

The declaration type `C < X0 <: T0>, …​, Xn <: Tn > = U` is well-formed provided:


## Making a loop 

### For loop 

```motoko
    for(i in Iter.range(0,size-1)){
      Debug.print(i);
    };
```

### Labeled loop

```Motoko

label l loop {
  i += 1;
  Debug.print(" I am in the fucking loop"); 
  Debug.print(debug_show(i));
  if(i >= 10)
    break l;
}
```

### while loop

```Motoko
     public func OurLoop() {

        var i = 0;
        while(i < 10) {
        i += 1;
        Debug.print(" I am in the fucking loop"); 
        Debug.print(debug_show(i));
        }
    };
```


## Option type

`?Nat`
Null Break `Nat!`



## Custom Type

```motoko

public type Person = {
  name : Text;
  age : Nat;
};

let tom : Person = {
  name = "Tom Cruise";
  age = 59;
};
```

## UnitTests

[DocumentaitonLink](https://kritzcreek.github.io/motoko-matchers/Matchers.html)


### Bool test

` M.equals(T.bool(true))),`

### Full test
```motoko
import M "mo:matchers/Matchers";
import T "mo:matchers/Testable";
import S "mo:matchers/Suite";


let suite = S.suite("My test suite", [
    S.suite("Nat tests", [
        S.test("10 is 10", 10, M.equals(T.nat(10))),
        S.test("5 is greater than three", 5, M.greaterThan<Nat>(3)),
    ])
]);
S.run(suite)
```

### Switch

```motoko
switch x { case (pat1) e1; …; case _ en }
```

### Assert

```motoko
import M "mo:matchers/Matchers";
import T "mo:matchers/Testable";

assertThat(5 + 5, M.equals(T.nat(10)));
assertThat(5 + 5, M.allOf<Nat>([M.greaterThan(8), M.lessThan(12)]));
assertThat([1, 2], M.array([M.equals(T.nat(1)), M.equals(T.nat(2))]));
```
## Types

### Questions

- [ ] Iters?
- [ ] Func?
- [ ] Trie?
- [ ] AssocList?

## AssocList

LinkedList - basically

### Buffer

`import Buffer "mo:base/Buffer";
let b:Buffer = Buffer.Buffer<Nat>(5);` - importing type

`Buffer.fromVarArray<Nat>(var 0,1,2,3)).toArray()`

### Iter

```motoko
    for(i in Iter.range(0,size-1)){
      Debug.print(i);
    };
```

### HashMap

```motoko
 let users = HashMap.HashMap<Principal, Text>(0, Principal.equal, Principal.hash);

```

### Text

#### `concat`

```motoko
	let textA = "Hello ";
	let textB = "World!";
	let textOut = Text.concat(textA,textB);
	Debug.print(debug_show(textOut));
```

## Debug

`import Debug "mo:base/Debug";`
`Debug.show(debug_show(iter.size()));`

##  Terms

Actor - is a class canister( I get a canister 
Modules -  Set of functions or even a class or variables
Classes  - is part of the module but is seprate class each one by one.

If using Cllass make sure that output is  *stable*!!!


