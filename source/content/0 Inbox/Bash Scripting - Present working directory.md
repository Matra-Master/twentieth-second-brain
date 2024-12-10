Apparently in bash you can get the working directory from where a script is **called** with this:
``` bash
script_dir=$(cd $(dirname"${BASH_SOURCE[0]}") && pwd)
```