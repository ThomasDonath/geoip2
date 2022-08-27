# geoip2

golang implementation of MaxMind's GeoIP2 Precision Services

modified by me: add option to decide wether to use the free or paid version. To use the free edition set *UseFreeApi=true* before any request.

## Example

Simple example to use the maxmind realtime api to perform a geo-query.  While City
takes an optional ```context.Context``` parameter, you can pass in nil if you don't
care to use this.

```go
package main

import (
	"os"
	"encoding/json"

	"github.com/savaki/geoip2"
)

func main() {
	api := geoip2.New(os.Getenv("MAXMIND_USER_ID"), os.Getenv("MAXMIND_LICENSE_KEY"))
	resp, _ := api.City(nil, "1.2.3.4")
	json.NewEncoder(os.Stdout).Encode(resp)
}
```
