debug is a simple library for Go that allows you to optionally debug your executable based on env variables.

# Usage

Simply add debug.Self() to your main function as shown below:

```
import (
    "github.com/edwarnicke/debug"
)

func main() {
    if err := debug.Self(); err != nil {
        log.Infof("%s", err)
    }
...
}
```

will cause your application to log out:

```
Setting env variable DLV_LISTEN_{{executable name}} to a valid dlv '--listen' value will cause the dlv debugger to execute this binary and listen as directed.
```

thus informing you of what env variable to set to a valid dlv listener value to trigger debugging.

So if your application where named 'forwarder', you'd see:

```
Setting env variable DLV_LISTEN_FORWARDER to a valid dlv '--listen' value will cause the dlv debugger to execute this binary and listen as directed.
```

and setting the env variable:

```
export DLV_LISTEN_FORWARDER=:50000
```

would cause your applicaton to exec itself over with dlv with arguments to run the application itself.
