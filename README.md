prep: run `npm install`

## Case 1

b depends on @a/a, and a.ts is available to the compiler

tsc, case 1: OK
```
rm -rf out; node node_modules/typescript/lib/tsc.js -p tsconfig-1.json; echo $?
0
```

bazeltsc, case 1: OK
```
rm -rf out; node node_modules/bazeltsc/dist/bazeltsc.js -p tsconfig-1.json; echo $?
0
```

## Case 2

b depends on @a/a, but only the a type declaration (a.d.ts) is available to the compiler

tsc, case 2: OK
```
rm -rf out; node node_modules/typescript/lib/tsc.js -p tsconfig-2.json; echo $?
0
```

bazeltsc, case 2: FAIL
```
rm -rf out; node node_modules/bazeltsc/dist/bazeltsc.js -p tsconfig-2.json; echo $?
b/b.ts(1,21): error TS2307: Cannot find module '@a/a'.
1
```
