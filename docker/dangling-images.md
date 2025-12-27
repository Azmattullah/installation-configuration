To **list all dangling Docker images** and **remove them**, use these commands:

### List dangling images

```bash
docker images -f "dangling=true"
```

### Remove all dangling images

```bash
docker image prune
```

This will prompt for confirmation.

### Remove dangling images **without confirmation**

```bash
docker image prune -f
```

### One-liner (list IDs, then delete)

```bash
docker rmi $(docker images -f "dangling=true" -q)
```

Note: Dangling images are **unused layers** (often from failed or repeated builds) and are generally safe to delete.
