[Stern](https://github.com/wercker/stern) is a tool that attempts to overcome some of these shortcomings.



There are two ways to specify the pods whose logs we want to see:

* `-l` followed by a selector expression (like with many `kubectl` commands), and
* with a "pod query," i.e. a regex used to match pod names

These two ways can be combined if necessary

1. View the logs for all the pingpong containers

```execute
stern pingpong
```
