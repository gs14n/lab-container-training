The `--tail N` flag shows the last N lines for each container
*(Instead of showing the logs since the creation of the container)*

The `-t` / `--timestamps` flag shows timestamps for each log


1. Only view new logs and print timestamps

```execute
stern --tail 1 --timestamps pingpong
```

3. Use stern with a selector to view logs for all pods with the label `app`:

```execute
stern -l app --tail 1
```
