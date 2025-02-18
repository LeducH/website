---
title: "Coding Conventions"
linkTitle: "Coding Conventions"
weight: 80
type: "docs"
---

cert-manager, like most Go projects, delegates almost all stylistic choices to `gofmt`,
with `goimports` on top for organizing imports. Broadly speaking, if you set your editor to run
`goimports` when you save a file, your code will be stylistically correct.

cert-manager generally also follows the Kubernetes
[coding conventions](https://www.kubernetes.dev/docs/guide/coding-convention/) and the Google
[Go code review comments](https://github.com/golang/go/wiki/CodeReviewComments).

## Organizing Imports

Imports should be organized into 3 blocks, with each block separated by two newlines:

```go
import (
	"stdlib"

	"external"

	"internal"
)
```

An example might be the following, taken from
[`pkg/acme/accounts/client.go`](https://github.com/jetstack/cert-manager/blob/0c71fe7795858b96cabcddabf706d997cd2fba3f/pkg/acme/accounts/client.go):

```go
import (
	"crypto/rsa"
	"crypto/tls"
	"net"
	"net/http"
	"time"

	acmeapi "golang.org/x/crypto/acme"

	acmecl "github.com/jetstack/cert-manager/pkg/acme/client"
	acmeutil "github.com/jetstack/cert-manager/pkg/acme/util"
	cmacme "github.com/jetstack/cert-manager/pkg/apis/acme/v1"
	"github.com/jetstack/cert-manager/pkg/metrics"
	"github.com/jetstack/cert-manager/pkg/util"
)
```

Once this manual split of standard library, external and internal imports has been made, it will be
enforced automatically by `goimports` when executed in the future.
