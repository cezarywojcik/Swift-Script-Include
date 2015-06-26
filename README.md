# Swift Script Include

Because running Swift in command-line doesn't support including other files, I made a quick Python script that takes in an input file and replaces all instances of `include somefile.swift` with the contents of that file. This happens recursively so that included files can also include other files.

## `swiftinclude.py`

The Python script needs an input file and an output file. By default, the input file is `main.swift`, and the output file is `app.swift`. You can also specify your own input and output files:

```bash
./swiftinclude.py -i input.swift -o output.swift
```

## `makefile`

The provided makefile assumes that you have a `main.swift` file and creates an `app.swift` file. Running `make` produces the `app.swift` file, and running `make run` produces the `app.swift` file and runs it.

## Example

After downloading the repo, simply run `make run`.

The included example will print `Hello, World!` to the console. The contents of the simple example is provided below.

### `main.swift`

```Swift
include "lib/test.swift"
helloWorld()
```

### `lib/test.swift`

```Swift
func helloWorld() {
    print("Hello, World!")
}
```

## Notes

* When using `include "filename.swift"`, double quotes are required.
* All paths are relative to the location of the Python script.
* If a file is included in multiple places, only the first instance of the `include` statement will be replaced with the file contents.

