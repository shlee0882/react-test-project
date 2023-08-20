
### 타입스크립트와 타입 정의 파일 설치 - 수동

```bash
$ npm install --save-dev typescript @types/node @types/react @types/react-dom
```

- 수동으로 설치하면 타입스크립트 설정파일인 tsconfig.json의 내용을 직접 설정해야함.
- 기존 js로 만들어진 App.js, index.js 파일유형을 tsx로 변경해줘야함

### 타입스크립트 템플릿 사용하기 - 자동

```bash
$ npx create-react-app [폴더명] --template=typescript
```

- 리액트에서 타입스크립트 사용하고 싶다면 create-react-app my-app --template=typescript 명령어로 자동으로 리액트 타입스크립트 설정 처리

### Emotion 설치

```bash
$ npm install --save @emotion/react @emotion/styled
```

### 절대경로 설정

##### tsconfig.json 파일에 compilerOptions의 "baseUrl": "src" 추가

```js
{
  "compilerOptions": {
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noFallthroughCasesInSwitch": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "baseUrl": "src"
  },
  "include": [
    "src"
  ]
}
```


### Prettier 설치

```bash
$ npm install --save-dev prettier
```

##### .prettierrc.js 생성

```js 
module.exports = {
    singleQuote: true, // 싱글쿼트를 주로 사용하도록 설정
    trailingComma: 'all', // 콤마를 추가할수 있다면 콤마 추가
    printWidth: 100, // 한 줄로 작성할 수 있는 최대 코드 문자 수 설정
};
```

##### package.json 내용 추가

```js
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "format": "prettier --check ./src",
    "format:fix": "prettier --write ./src"
  },
```

##### 잘못된 내용 체크

```bash
$ npm run format
```

##### 파일 검사 수정 

```bash
$ npm run format:fix
$ npm run format
```


### ESLint 설치

```bash
$ npm install eslint --save-dev
```

##### ESLint 설정

```bash
$ npx eslint --init
```


##### .eslintrc.js 파일 수정

```js
module.exports = {
    "settings": {
        "react": {
            "version": "detect", 
        },
    },
    "env": {
        "browser": true,
        "es2021": true
    },
    "extends": [
        "eslint:recommended",
        "plugin:@typescript-eslint/recommended",
        "plugin:react/recommended"
    ],
    "overrides": [
        {
            "env": {
                "node": true
            },
            "files": [
                ".eslintrc.{js,cjs}"
            ],
            "parserOptions": {
                "sourceType": "script"
            }
        }
    ],
    "parser": "@typescript-eslint/parser",
    "parserOptions": {
        "ecmaVersion": "latest",
        "sourceType": "module"
    },
    "plugins": [
        "@typescript-eslint",
        "react"
    ],
    "rules": {
        'react/react-in-jsx-scope' : 'off',
    }
}
```

### 초기 셋팅 정리

- 절대경로 설정 (tsconfig.json)
- Emotion, Prettier, ESLint 설치

``` bash
npm install --save @emotion/react @emotion/styled
npm install --save-dev prettier eslint
```

- .prettierrc.js 파일 생성 및 수정
- .eslintrc.js 파일 수정
- package.json 수정

``` bash
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "format": "prettier --check ./src",
    "format:fix": "prettier --write ./src",
    "lint": "eslint ./src",
    "lint:fix": "eslint --fix ./src"
  },

// prettier, eslint 검사 후 수정
$ npm run format
$ npm run format:fix
$ npm run lint
$ npm run lint:fix
```

- useState 훅 사용 - 데이터 변경 
- interface props 사용으로 컴포넌트 분리
