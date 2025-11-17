# 🚀 React Query (TanStack Query) – Complete Notes

React Query helps manage server state (data fetched from APIs). It handles:
- caching
- background refetching
- updating stale data
- mutations
- loading/error states

It removes the need for `useState + useEffect + fetch` everywhere.

---

## 📌 1. QueryClient Setup

Before using React Query in any component, wrap your app:

```javascript
const queryClient = new QueryClient();

createRoot(document.getElementById('root')).render(
  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>
);
```

This gives your entire app access to the QueryClient.

---

## 📌 2. Example Products API (In-Memory)

```javascript
export const products = [
  { id: 1, title: "Product 1" },
  { id: 2, title: "Product 2" },
  { id: 3, title: "Product 3" }
];
```

**Fetch function (simulates API delay)**

```javascript
export async function fetchProductData() {
  await new Promise((resolve) => setTimeout(resolve, 1000));
  return products;
}
```

**Add product mutation (simulated)**

```javascript
export async function addProduct(productData) {
  await new Promise((resolve) => setTimeout(resolve, 1000));

  const newProduct = {
    id: products.length + 1,
    title: productData
  };

  products.push(newProduct);

  return newProduct;
}
```

---

## 📌 3. useQuery – Fetching Data

```javascript
const { data, isLoading } = useQuery({
  queryKey: ['products'],
  queryFn: fetchProductData
});
```

**What happens?**

| Part | Meaning |
|------|---------|
| `queryKey` | A unique ID for caching (like a state name) |
| `queryFn` | The function that fetches data |
| `isLoading` | True when loading |
| `data` | Cached server response |

✔️ React Query caches the products  
✔️ When the component re-renders, it does NOT refetch unless needed

---

## 📌 4. useMutation – Adding a Product

```javascript
const { mutateAsync: handleAddNewProduct } = useMutation({
  mutationFn: addProduct,
  onSuccess: () => {
    queryClient.invalidateQueries(['products']);
  }
});
```

**What happens?**

| Part | Meaning |
|------|---------|
| `mutationFn` | The API function to run (POST/PUT/DELETE) |
| `mutateAsync` | Async version of mutate() |
| `onSuccess` | Runs after the mutation succeeds |
| `invalidateQueries` | Forces refetch of affected query |

**Why invalidateQueries?**

Because products changed → refetch products. This updates the UI automatically.

---

## 📌 5. Handling Input & Button

```javascript
function handleChange(e) {
  setProductTitle(e.target.value);
}
```

**Button event:**

```javascript
async function handleClick() {
  await handleAddNewProduct(productTitle);
  setProductTitle('');
}
```

---

## 📌 6. Final UI Rendering

```javascript
{isLoading && <h1>Fetching Data</h1>}

{data?.length > 0 &&
  data.map((item) => <h4 key={item.id}>{item.title}</h4>)
}
```

---

## 🔥 7. How the Full Flow Works

**Step-by-step:**

1. Component mounts
2. `useQuery` → fetchProductData() runs
3. Data is cached
4. User types and clicks Add Product
5. `useMutation` calls `addProduct()`
6. After `onSuccess`, React Query:
   - invalidates `['products']` query
   - refetches products
   - updates UI

---

## 📘 8. Why React Query is Better Than useEffect + fetch

| useEffect/fetch | React Query |
|----------------|-------------|
| Manual loading state | Built-in |
| Manual error handling | Built-in |
| No cache | Auto cache |
| Refetch manually | Auto refetch |
| Repeated network calls | Cached responses |
| No mutation system | Full mutation pipeline |

React Query makes server-state logic clean, predictable, efficient.

---

## 🧠 9. Important Hooks Overview

### `useQuery`
Used for GET / fetch operations.

### `useMutation`
Used for POST / PUT / PATCH / DELETE.

### `useQueryClient`
Used to:
- invalidate queries
- manually update cache
- reset cache

---

## 🎯 11. Short Summary

- `useQuery` → fetch data & cache
- `useMutation` → create/update/delete data
- `invalidateQueries` → refresh data after mutation
- React Query automates loading, error, caching, and refetching
- Your custom API simulates real backend
- UI updates automatically when query is invalidated

---

# ⭐ Most Commonly Used React Query Features

## 1️⃣ useQuery (FETCHING DATA)

You will use this the most.

- Fetch API data
- Cache it
- Get loading/error states
- Auto-refetch when needed

```javascript
const { data, isLoading, error } = useQuery({
  queryKey: ['products'],
  queryFn: fetchProducts
});
```

---

## 2️⃣ useMutation (POST/PUT/DELETE)

Used for changing data:
- Create
- Update
- Delete

```javascript
const { mutate, mutateAsync } = useMutation({
  mutationFn: addProduct
});
```

You'll use:
- `mutate()` for direct calls
- `mutateAsync()` when you want async/await

---

## 3️⃣ useQueryClient (MANAGING CACHE)

After adding/updating/deleting data, you must refresh queries.

**Most common usage:**

### 🔥 `invalidateQueries()`

Tells React Query: "Refetch this data."

```javascript
const queryClient = useQueryClient();

queryClient.invalidateQueries(['products']);
```

You use this almost every time after a mutation.

### ⭐ Common Pattern: Mutation + Refetch

```javascript
const mutation = useMutation({
  mutationFn: addProduct,
  onSuccess: () => {
    queryClient.invalidateQueries(['products']);
  }
});
```

**This is the standard pattern in every project.**

---

## 4️⃣ Useful Query States

### For useQuery:
- `isLoading` → First time loading
- `isFetching` → Background refetch
- `error` → For error UI
- `data` → Final data

### For useMutation:
- `isPending` → While mutation running
- `isError` → When API fails
- `isSuccess` → When mutation completes

**Example:**

```javascript
const { mutate, isPending } = useMutation(...);

if (isPending) return <p>Adding...</p>
```

---

## 5️⃣ refetch() (Manual Refetch)

Sometimes you want to trigger fetch manually.

```javascript
const { data, refetch } = useQuery({
  queryKey: ['products'],
  queryFn: fetchProducts
});

<button onClick={() => refetch()}>Refresh</button>
```

---

## 6️⃣ Query Options (Most Used)

### 🔹 refetchOnWindowFocus

Disable refetch when switching tabs:

```javascript
useQuery({
  queryKey: ['products'],
  queryFn: fetchProducts,
  refetchOnWindowFocus: false
});
```

### 🔹 staleTime

How long data stays "fresh" (no refetch):

```javascript
staleTime: 1000 * 10 // 10 seconds
```

---

## ⭐ Most Common Things (Short List)

You should remember just these 6:

1. **useQuery** → fetch
2. **useMutation** → add/update/delete
3. **useQueryClient** → manage cache
4. **invalidateQueries** → refresh UI
5. **refetch** → manual refresh
6. **isLoading / isFetching / isPending** → UI loading states

**These six things cover 95% usage in daily development.**

---

##  Most Used Real-Life Workflow

This is the pattern used in almost every company:

```javascript
const { data } = useQuery({
  queryKey: ['users'],
  queryFn: fetchUsers
});

const mutation = useMutation({
  mutationFn: addUser,
  onSuccess: () => {
    queryClient.invalidateQueries(['users']);
  }
});
```
