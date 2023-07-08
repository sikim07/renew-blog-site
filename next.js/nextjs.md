---
title: 'NextJS 란?'
date: 2021-07-26 21:01:20
category: 'next.js'
draft: false
---

## 배경

1. Code has to be bundled using a `bundler` like webpack and transformed using a compiler like Babel.
   코드는 webpack과 같은 `번들러`를 사용하여 번들링되고 Babel과 같은 컴파일러를 사용하여 변환되어야 합니다.

2. You need to do `production optimizations` such as code splitting.
   코드 분할과 같은 `프로덕션 최적화`를 수행해야 합니다.

3. You might want to statically pre-render some pages for performance and SEO. You might also want to use server-side rendering or client-side rendering.
   성능 및 SEO를 위해 일부 페이지를 정적으로 사전 렌더링할 수 있습니다. 서버 측 렌더링 또는 클라이언트 측 렌더링을 사용할 수도 있습니다.

4. You might have to write some server-side code to connect your React app to your data store.
   React 앱을 데이터 저장소에 연결하기 위해 서버 측 코드를 작성해야 할 수도 있습니다.

위 고려사항들에 대한 대안이 `NextJS`이다.

## 제공 기능

- 직관적인 페이지 기반 라우팅 시스템(동적 경로 지원 포함)
- 사전 렌더링, 정적 생성(SSG) 및 서버 측 렌더링(SSR) 모두 페이지 단위로 지원됩니다.
- 더 빠른 페이지 로드를 위한 자동 코드 분할
- 최적화된 프리페칭을 통한 클라이언트 측 라우팅
- 내장 CSS 및 Sass 지원 및 모든 CSS-in-JS 라이브러리 지원
- Fast Refresh를 지원하는 개발 환경
- Serverless Functions로 API 엔드포인트를 빌드하기 위한 API 경로 완전히 확장 가능