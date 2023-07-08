---
title: 'NextJS Tutorial 2'
date: 2021-08-01 21:40:47
category: 'next.js'
draft: false
---

## Navigate Between Pages


### Download Starter Code (Optional)

```sh
npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn-starter/tree/master/navigate-between-pages-starter"
```


### Pages in Next.js

Next.js에서는 React Component를 `pages` 디렉터리에서 가져온다
페이지는 파일 이름으로 지정한다.
- `pages/index.js` 는 `/`로 라우트된다.
- `pages/posts/first-posts.js`는 `/posts/first-post`로 라우드 된다.

`pages/index.js`파일은 이미 있기 때문에 `pages/posts/first-post.js`를 만들어 확인해본다.

### Create a New Page

`pages` 디렉터리 아래 `posts` 디렉터리를 생성한다.
`posts`디렉터리 안에 `first-post.js` 파일을 생성하고 아래 구문을 작성한다.

```js
export default function FirstPosts() {
    return <h1>First Post</h1>
}
```


'http://localhost:3000/posts/first-post' 에서 확인이 가능하다.

### Link Component

Next.js에서는 `next/link`에서의  `Link` 컴퍼넌트로 `<a>` 태그를 사용한다.
`<Link>`는 다른 페이지로 client-side navigation 할수 있게 한다.

### Using `<Link>`

`pages/index.js`파일을 열어 Link 컴퍼넌트를 `next/link`에서 import한다.

```js
import Link from 'next/link'
```

h1 태그를 아래와 같이 작성한다.

```js
<h1 className="title">
    Learn <a href="https://nextjs.org">Next.js!</a>
</h1>
```


그리고 아래와 같이 수정한다.

```js
<h1 className="title">
    Read{' '}
    <Link href="/posts/first-post">
        <a>this page!</a>
    </Link>
</h1>
```

(`{' '}`는 여러 라인에서 텍스트를 나눌때 사용한다)


`pages/posts/first-post.js`를 아래와 같이 수정한다.

```js
import Link from 'next/link'

export default function FirstPost() {
    return (
        <>
            <h1>Fist Post</h1>
            <h2>
                <Link href="/">
                    <a>Back to home</a>
                </Link>
            </h2>
        </>
    )
}
```


위에서 보다시피, Link 컴퍼넌트는 a태그와 비슷하다. `<a href="...">`대신 `<Link href="...">`을 사용하는 것만 다르다.


### Code splitting and prefetching

Next.js는 code splitting을 자동으로 수행하기 때문에 각 페이지는 필요한 페이지만 로드한다. 이는 홈페이지가 렌더되면 다른페이지의 코드들은 제공되지 않는다.

따라서 수 백개의 페이지가 있다고 하더라도 홈페이지 로드가 빠르게 수행될 수 있다.

특정 페이지 로드를 위한 코드는 'isolated'되어있기 때문에 특정 페이지에서 에러가 발생해도 나머지 페이지들은 정상적으로 작동한다.

`Link` 컴퍼넌트를 이용하여 보여지는 브라우저의 viewport는 자동적으로 백그라운드에서 `prefetches`된다. link를 클릭할 때 코드의 경로 페이지가 백그라운드에서 로드된 채 보여진다.