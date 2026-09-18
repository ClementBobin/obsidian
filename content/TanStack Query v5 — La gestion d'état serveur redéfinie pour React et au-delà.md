---
tags: [veille, frontend, react, state-management, typescript, data-fetching]
date: 2025-09-11
source: https://tanstack.com/query
---

# 🔄 TanStack Query v5 — La gestion d'état serveur redéfinie pour React (et au-delà)

> [!info] 📌 Veille Technologique — DIIAGE 2028
> Librairie de synchronisation asynchrone et de cache serveur pour React, Vue, Solid, Angular.

---

## 🧭 Pourquoi c'est pertinent

Un composant React qui fetche des données, c'est toujours le même problème : loading state, error state, refetch au focus, cache invalidation, pagination… TanStack Query (ex-React Query) **encapsule tout ça** avec une API élégante et une v5 entièrement refondée en 2024.

La distinction fondamentale qu'il impose : **état client** (ce que l'utilisateur a tapé) ≠ **état serveur** (ce qui vient de l'API). Ce sont deux problèmes différents qui méritent deux solutions différentes.

---

## ⚙️ Exemple concret

```typescript
import { useQuery, useMutation, useQueryClient } from '@tanstack/react-query'

// Fetch avec cache, retry, loading/error state automatiques
function ArticleList() {
  const { data, isPending, isError } = useQuery({
    queryKey: ['articles'],
    queryFn: () => fetch('/api/articles').then(r => r.json()),
    staleTime: 1000 * 60 * 5, // données fraîches pendant 5 min
  })

  if (isPending) return <Skeleton />
  if (isError) return <ErrorBanner />
  return data.map(a => <ArticleCard key={a.id} {...a} />)
}

// Mutation avec invalidation automatique du cache
function CreateArticle() {
  const queryClient = useQueryClient()
  
  const mutation = useMutation({
    mutationFn: (article) => fetch('/api/articles', { method: 'POST', body: JSON.stringify(article) }),
    onSuccess: () => queryClient.invalidateQueries({ queryKey: ['articles'] }),
  })

  return <button onClick={() => mutation.mutate({ title: 'Nouveau' })}>Créer</button>
}
```

---

## 🧩 Nouveautés v5

- **API unifiée** : `useQuery` et `useSuspenseQuery` avec la même signature — plus de surcharge d'API
- **`infiniteQuery` simplifié** : `initialPageParam` explicite, `getNextPageParam` plus clair
- **Devtools repensés** : timeline visuelle des requêtes, inspection du cache
- **Optimistic updates first-class** : `onMutate` + rollback en cas d'erreur simplifié
- **TypeScript strict** : types inférés end-to-end sans casting

---

## 💡 Pourquoi c'est utile pour nous

Dans CYNA (React web) ou dans tout projet qui consomme une API REST ou GraphQL, TanStack Query remplace avantageusement le pattern `useEffect + useState + fetch` qui est fragile et verbose. C'est aussi un excellent sujet d'**architecture de state management** pour un mémoire ou une soutenance : il illustre la séparation des responsabilités entre état local et état distant.

---

## 🔗 Ressources

- 🌐 [Site officiel — tanstack.com/query](https://tanstack.com/query)
- 📖 [Docs v5](https://tanstack.com/query/latest/docs/framework/react/overview)
- 🐙 [GitHub — TanStack/query](https://github.com/TanStack/query)
- 📝 [Guide de migration v4 → v5](https://tanstack.com/query/latest/docs/framework/react/guides/migrating-to-v5)
