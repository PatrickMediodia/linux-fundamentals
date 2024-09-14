**Redirects**
`<input> > <output>` - overwrites the output file contents
`<input> >> <output>` - appends the output file contents

`<command> < <output>` - redirect command to the left
`<command> << <end sequence>` - will allow multiple commands until the end sequence is met
`<command> <<< "<string>"` - used to redirect a string to a command

`$?` - returns the exit code of the last command executed

**Testing for Equality**
`[ 1 = 1 ]`
`[ 1 -eq 1 ]`

**Exit Code**
`0` - executed without any issues
`1` - error

**If Else Statements**
```
#!/bin/bash

if [ ${1,,} = patrick ]; then
        echo "Welcome"
elif [ ${1,,} = help ]; then
        echo "Enter your username"
else
        echo "I do not know who you are"
fi
```

`${1,,}` - parameter expansion allows you to ignore cases in parameter values
`fi` - required to close your if statements

**Switch Case Statements**
```
#!/bin/bash

case ${1,,} in
        patrick)
                echo "Hello" $1;;
        help)
                echo "Enter your name";;
        *)
                echo "Not a valid command";;
esac
```

