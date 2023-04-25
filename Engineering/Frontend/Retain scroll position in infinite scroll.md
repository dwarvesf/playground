---
tags: engineering/frontend, frontend, infinite-scroll, swr, swr-infinite, web-design, accessibility, usability, client-side-storage, session-storage
author: Nguyen Dinh Nam
github_id: nguyend-nam
date: 2023-04-24
icy: 10
---

## Infinite scroll - Benefits and Challenges

Have you ever come across a website or application that dynamically loads and displays more content as you scroll? This is what we call an infinite scroll. This technique is often used to create a seamless, continuous browsing experience that feels natural and intuitive.

Infinite scroll has become a popular web design technique in recent years, as it offers several benefits over traditional pagination models such as reducing page load times or minimizing the need for users to click through multiple pages to find the content they are looking for. However, it is important to design and implement infinite scroll carefully, as it can also present some challenges for accessibility and usability. One of the most common and painful usability issues with infinite scroll is losing your previous scroll position when going back after you click on an item to view its detail (and of course, is navigated to another page).

![](http://www.explainxkcd.com/wiki/images/5/56/infinite_scrolling.png)

*Image Source: [https://www.explainxkcd.com](https://www.explainxkcd.com/wiki/index.php/1309:_Infinite_Scrolling)*

## Solution

There are many ways to come up with a workaround, but most of the solutions have one thing in common: storing the scroll position in a client-side storage. In this article, we will show you an approach using the session storage, assuming that the infinite scroll is implemented using [`useSWRInfinite`](https://swr.vercel.app/docs/pagination.en-US#useswrinfinite).

> Learn more about [client-side storage](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Client-side_storage)

```javascript
export const LIST_STORAGE_KEY = 'list-states'

export default function createRestoreSWRInfinityPositionStore<
	T extends SWRInfiniteResponse<any, any>,
>(storeKey = LIST_STORAGE_KEY) {
	function useRestorePosition({ swr }: { swr: T }) {
		// ...
	}
	
	function handleSaveSWRStates({ swr }: { swr: T }) {
		// ...
	}
	
	return { useRestorePosition, handleSaveSWRStates }
}
```

Let's begin by creating a `createRestoreSWRInfinityPositionStore` that takes in a key that we will use to store and retrieve data from the session storage.

We will also implement two functions inside, one to handle the behaviors before routing happens, and another one for those when we go back to the page and want to retain the scroll position. Both of them accept the parameter of `swr` which is the [response](https://swr.vercel.app/docs/pagination.en-US#return-values) of the `useSWRInfinite`.

```javascript
function handleSaveSWRStates({ swr }: { swr: T }) {
	sessionStorage.setItem(
		storeKey,
		JSON.stringify({ swrSize: swr.size, scrollPos: window.scrollY }),
	)
}
```

As you can see, the function above simply stores an object with `swrSize` and `scrollPos` field to the session storage. When a user clicks on an item and is navigated to the detail page, we call this function along with the routing function to store the vertical scroll position (`scrollPos`) and also the number of pages (or a group of several consecutive items) that infinite scroll already loaded (`swrSize`).

```javascript
function useRestorePosition({ swr }: { swr: T }) {
	const docHeight = document?.documentElement.scrollHeight || 0
	const listStates = JSON.parse(sessionStorage.getItem(storeKey) || '{}')
	
	useEffect(() => {
		if (typeof listStates.scrollPos !== 'number') return undefined
		
		if (docHeight > listStates.scrollPos) {
			window.scrollTo(0, listStates.scrollPos)
			sessionStorage.removeItem(storeKey)
		}
	}, [docHeight, listStates.scrollPos])
	
	useEffect(() => {
		if (typeof listStates.swrSize !== 'number') return undefined
		
		if (listStates.swrSize > 1) {
			swr.setSize(listStates.swrSize)
		}
	}, [listStates.swrSize, swr])
}
```

The hook `useRestorePosition` is called in the listing page that uses the infinite scroll technique, so that everytime we visit the page, the two `useEffect`s help us to retrieve the number of loaded pages of the items list and the vertical scroll position. The `scrollPos` is used for scrolling the page to the previous position. The `swrSize`, on the other hand, is passed to the `setSize` function to tell `swr` how many pages already loaded before we were navigated to the item detail page.

This makes sense since as mentioned above, when user clicks on an item and is navigated to the detail page, we will store those data to the session storage, and when user wants to go back to the listing page, the hook `useRestorePosition` can retrieve those data and the page will be scrolled to the previous position. After calling `window.scrollTo(0, listStates.scrollPos)`, remove the relating data from the session storage to prevent unwanted scrolling behaviors of the page in the future.

## Reference

- https://www.explainxkcd.com/wiki/index.php/1309:_Infinite_Scrolling