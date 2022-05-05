# AngularTestingJest

Angular Unit Testing with Jest Library.

## 1. Remove all Karma and Jasmine Dependencies

```bash
npm uninstall @types/jasmine jasmine-core karma karma-chrome-launcher karma-coverage karma-jasmine karma-jasmine-html-reporter
```

## 2. Clean Up Unused Files

delete `karma.conf.js` and `src/test.ts`

## 3. Install Required Jest Packages

```bash
npm install -D jest jest-preset-angular @types/jest
```

## 4. Configure Jest with Angular

In the project root create a file called `setup-jest.ts` with the following contents :-

```ts
import "jest-preset-angular/setup-jest";
```

And add the following to the `package.json`

```json
{
  "jest": {
    "preset": "jest-preset-angular",
    "setupFilesAfterEnv": ["<rootDir>/setup-jest.ts"],
    "globalSetup": "jest-preset-angular/global-setup"
  }
}
```

Finally adjust the `tsconfig.spec.json` to be :-

```json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./out-tsc/spec",
    "module": "CommonJs",
    "types": ["jest"]
  },
  "include": ["src/**/*.spec.ts", "src/**/*.d.ts"]
}
```

## 5. Add the Test Scripts

In `package.json` add the following scripts

```json
"test": "jest",
"test:watch": "jest --watch",
"test:coverage": "jest --coverage",
```
