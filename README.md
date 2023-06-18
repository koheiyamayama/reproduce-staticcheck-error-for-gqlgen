# What happened
I have staticcheck's error during upgrading gqlgen from v0.17.31 to v0.17.33.
The method to reproduce this error is below.
```
$ cd /path/to/gqlgen-reporduce-error
$ go generate ./...
$ staticcheck --version
staticcheck 2023.1.3 (v0.4.3)
$ staticcheck ./...
graph/generated.go:3258:2: unreachable case clause: github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.Post will always match before github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.TweetPost (SA4020)
graph/generated.go:3260:2: unreachable case clause: github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.Post will always match before *github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.TweetPost (SA4020)
graph/generated.go:3265:2: unreachable case clause: github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.Post will always match before github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.FacebookPost (SA4020)
graph/generated.go:3267:2: unreachable case clause: github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.Post will always match before *github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.FacebookPost (SA4020)
graph/generated.go:3272:2: unreachable case clause: github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.Post will always match before github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.InstagramPost (SA4020)
graph/generated.go:3274:2: unreachable case clause: github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.Post will always match before *github.com/koheiyamayama/gqlgen-reproduce-error/graph/model.InstagramPost (SA4020)
```

# minimal schema
- There are schema files in graph/schema directories.

# What I expected
No staticcheck error

# versions
- golang
  - go1.20.4 darwin/arm64
- gqlgen
  - v0.17.33

# memo
I think that I read graph/generated.go. It is probably no problem.
But I'm glad if staticcheck error doesn't happen.
