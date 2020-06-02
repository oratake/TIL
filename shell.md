# Shell

## Shebang `#!/bin/bash`

Keyword: Shebang, シバン, シェバン, /bin/sh

大体以下で解決した  
https://qiita.com/mohira/items/566ca75d704072bcb26f

Shebangはインタプリタの指定になっているので、 `#!` 以降が引数として渡される

./sample04.rb

```
#!/usr/bin/env ruby
// ruby script
...
```

```
$ /usr/bin/env ruby ./sample04.rb
↑等価↓
$ ./sample04.rb
```
