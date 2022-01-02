# Lecture 06 - Async List/Detail in React

## From Scratch Demo: Adopt-a-Dog

## Half-Baked Project: Beanie Babies

## New fetch every time the 'page' changes
```js
  useEffect(() => {
    async function fetch() {
      const from = page * perPage - perPage;
      const to = page * perPage
      const beanies = await getBeanieBabies(from, to);

      setBeanieBabies(beanies);
    }

    fetch();
  }, [page]);
  ```