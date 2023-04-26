## package.json

패키지의 버전을 명시, 관리해주는 파일.
현재 프로젝트에 관한 정보와 패키지 매니저(npm, yarn)를 통해 설치한 모듈의 의존성을 관리한다.

## 1. 기본 설정

npm을 사용하는데 기본적으로 필요한 필드.
npm init을 하면 초기의 package.json 파일을 생성할 수 있다.
JSON 포맷으로 이루어져 있다.

```js
{
  "name": "payments",
  "version": "0.1.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

name(프로젝트의 이름)과 version(프로젝트의 버전)은 반드시 포함되어야 한다.

## 2. dependencies와 devDependencies

패키지를 설치하면 dependencies와 devDependencies로 나눠서 관리한다.
구분해서 패키지를 설치하면 빌드 시간도 줄이고, 배포할 때 불필요한 라이브러리를 포함하지 않아도 되는 장점이 있다.

### dependencies

- 일반적으로 의존하고 있는 패키지의 버전 정보이다.
- 애플리케이션 동작과 관련되어서 반드시 있어야 하는 것으로 배포를 할 때 포함해야 한다.
- npm install <package_name>을 통해 설치할 수 있다.

### devDependencies

- 개발중일 때 의존하고 있는 패키지의 버전 정보이다.
- 개발할 때만 필요한 라이브러리이기 때문에 배포할 때 포함하지 않는다.
- npm install <package_name> —save-dev 나 npm install <package_name> -D를 통해 설치할 수 있다.
