---
title: "A Tiny Custom React hooks for making request"
datePublished: Wed Nov 15 2023 00:04:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1crsl2000i09jubsuq7bcj
slug: a-tiny-custom-react-hooks-for-making-request

---

---
title: A Tiny Custom React hooks for making request
published: true
date: 2023-11-15 00:04:00 UTC
tags: Hooks
canonical_url: https://reactjsexample.com/a-tiny-custom-react-hooks-for-making-request/
---

# react-request

## Install

```
yarn add @blacktea/react-request
```

## Basic Usage

 ![A Tiny Custom React hooks for making request](https://cdn.hashnode.com/res/hashnode/image/upload/v1700148919956/b6b2e320-2bb5-410c-b789-e87a58b80838.jpeg)

```
import useRequest from '@blacktea/react-request'
import getFooApi from '@/utils/axios'

function App () {
  const [{ loading, error, data }, fetch] = useRequest(getFooApi)

  useEffect(() => { fetch() }, [fetch])

  if (loading) return 'loading'
  if (error) return 'error'

  return data && <div>{data}</div>
}
```

## More Example

> Queries are typically start with loading, we can create a `useQuery` function before we use.

```
function useQuery (api) {
  return useRequest(api, { loading: true })
}
```

### Query

```
function Query () {
  const [{ loading, error, data }, fetch] = useQuery(queryFooApi)

  useEffect(() => { fetch() }, [fetch])

  if (loading) return 'loading...'
  if (error) return 'error'

  // no need to check data
  return <div>{data}</div>
}
```

### Multi Query

```
function MultiQuery () {
  const [foo, fetchFoo] = useQuery(queryFooApi)
  const [bar, fetchBar] = useQuery(queryBarApi)

  useEffect(() => {
    fetchFoo()
    fetchBar()
  }, [fetchFoo, fetchBar])

  const renderContent = (state) => {
    const { loading, error, data } = state

    if (loading) return 'loading...'
    if (error) return 'error'

    return <div>{data}</div>
  }

  return (
    <div>
      {renderContent(foo)}
      {renderContent(bar)}
    </div>
  )
}
```

### Batch Query

```
function BatchQuery () {
  const batchFetchApi = () => Promise.all([queryFooApi(), queryBarApi()])
  const [{ loading, error, data }, fetch] = useQuery(batchFetchApi)

  useEffect(() => { fetch() }, [fetch])

  if (loading) return 'loading...'
  if (error) return 'error'

  const [foo, bar] = data

  return (
    <div>
      <div>{foo}</div>
      <div>{bar}</div>
      <button onClick={fetch}>refetch batch</button>
    </div>
  )
}
```

### Mutate

```
function Mutate () {
  const [{ loading, error, data }, mutate] = useRequest(mutateBazApi)
  const [value, setValue] = useState('')

  useEffect(() => {
    if (error) alert('error')
    if (data === 'success') alert('success')
  }, [error, data])

  return (
    <div>
      <input value={value} onChange={(e) => setValue(e.target.value)} />
      <button disabled={loading} onClick={() => mutate(value)}>submit</button>
    </div>
  )
}
```

## Api

```
type useRequest = (api, initialState) => [state, memoizedRequestCallback]
```

## GitHub

[View Github](https://github.com/BlackTea99/react_request?ref=reactjsexample.com)