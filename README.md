# CRA Boilerplate

자주 사용하는 라이브러리를 세팅한 CRA 보일러플레이트입니다. 매번 설치하기 번거로워서 만들었습니다.

## 사용한 라이브러리

- `Create React App`
- Package Manager: `yarn`
- Language: `TypeScript`
- Linter: `eslint-config-airbnb`, `eslint-config-airbnb-typescript`
- Code Formatter: `prettier`
- `husky`

## 사용 방법

### 1. 해당 보일러플레이트 프로젝트 복제

```bash
git clone https://github.com/heony704/cra-boilerplate.git newProjectName
```

### 2. 새로운 remote url 재설정

복제된 프로젝트의 remote url이 해당 보일러프로젝트를 향하기 때문에 재설정해줘야 합니다.

```bash
git remote set-url origin newRepositoryUrl
```

### 3. 프로젝트 이름 수정

`package.json` 파일의 `name` 값을 수정하세요.

### 4. 프로젝트 시작

```bash
yarn
yarn start
```

## 특이사항

`eslint-config-airbnb`를 설치할 때 peer dependencies를 함께 설치하는 명령어를 사용하면, 간혹 라이브러리 버전 관련 에러가 발생합니다.

기존 라이브러리의 종속성으로 인해 설치된 하위 라이브러리가 존재함에도 설치해버렸기 때문에 둘의 버전이 달라서 에러가 발생하는 것 같습니다.

그래서 peer dependencies를 몽땅 설치하는 대신 기존에 존재하는 라이브러리라면 `package.json`의 `resolutions`에 작성해 버전으로 인한 에러가 발생하지 않도록 버전을 통일시켰습니다.
