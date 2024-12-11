# Description

This repo contains some copy-pasta of [what essentially gets run](https://github.com/hashicorp/terraform-provider-kubernetes/blob/384d2da721fff5c90ba391dd42d4440be8d08d3a/internal/framework/provider/functions/manifest_decode_multi.go#L39-L55) by the kubernetes terraform provider when it attempts to decode a manifest file.

It shows how the size of a CRD affects allocations for figuring out how much memory terraform is going to take when processing a particular CRD.

# Running

```bash
./get_crd.sh
go test -bench=. -benchmem
```

Output should be something like:

```
goos: darwin
goarch: arm64
pkg: github.com/andrewstucki/crd-benchmark-decode
BenchmarkDecode/decode-11         	       5	 251167825 ns/op	69036873 B/op	  701073 allocs/op
PASS
ok  	github.com/andrewstucki/crd-benchmark-decode	2.581s
```