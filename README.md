# go_cobra_cli
Hacking around with creating CLIs using Go and Cobra


## Adding commands

`go-gobra add [myCmd]`. This will add the cmd at the root level, to add it as a child of the parent command:

1. move the generated `<myCmd>.go` into its own folder.
2. Make it public (capatalise the name)
3. import it into the `root.go` and call `rootCmd.AddCommand(<myPackage.myCmd>)`

see how net/net.go is configured to achieve this.

To make the subcommand itself take subcommands:

1. add a second package to the parent (go-gobra add [myCmd]) and move to the parent package
2. <parentCmd>.AddCommand(<childCmd>)

See `ping.go` for an example of a sub-command of net. E.g. this gives us the tree `go_cobra_cli -> net -> ping`.

Alternatively, `cobra add <new command> -p <parent command>` - does the same thing!
