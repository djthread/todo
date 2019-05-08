# Two Simple TODO List Implementations

This is just a quick comparison between two implementations of a simple todo
list, copied into this repository.

  * [`dnsbty/live_view_todos`](https://github.com/dnsbty/live_view_todos)
    Phoenix LiveView todo list to follow along with the tutorial on
    [https://dennisbeatty.com](http://dennisbeatty.com)
  * [`bradtraversy/angular-crash-todolist`](https://github.com/bradtraversy/angular-crash-todolist)
    Simple app for Angular crash course

## LiveView Version

1 sec to install 24 dependencies

Most of the code is in [the LiveView
module](live_view_todos/lib/live_view_todos_web/live/todo_live.ex) and its
related [template
file](live_view_todos/lib/live_view_todos_web/templates/todo/todos.html.leex).
The only other significant part in this example is the [context
module](live_view_todos/lib/live_view_todos/todos.ex) for the business logic of
managing todos, interacting with the database, etc.

**This version includes the backend service** with database persistance. Also,
many concerns are out of scope, for instance the frontend/backend interaction
API.

## Angular Version

15 sec to install 688 dependencies

It would seem that this one has more files, moving parts, complexity, and
things to learn. The important files to look at are in
[`src/app`](angular-crash-todolist/src/app).

This version does not include its required backend service.

## Lines of Code Comparison

```
$ cloc live_view_todos/lib
      20 text files.
      20 unique files.
       1 file ignored.

github.com/AlDanial/cloc v 1.80  T=0.02 s (987.7 files/s, 27499.0 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
Elixir                          17             93            168            236
EEx                              2              0              0             32
-------------------------------------------------------------------------------
SUM:                            19             93            168            268
-------------------------------------------------------------------------------
$ cloc angular-crash-todolist/src/
      38 text files.
      38 unique files.
       5 files ignored.

github.com/AlDanial/cloc v 1.80  T=0.03 s (1361.1 files/s, 27664.3 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
TypeScript                      22             96             98            353
CSS                              4             10              0             64
HTML                             7              2              0             52
JSON                             3              0              0             46
JavaScript                       1              1              2             28
-------------------------------------------------------------------------------
SUM:                            37            109            100            543
-------------------------------------------------------------------------------
```

### Lines We Need to Write

Many lines come free with the new app generators, but if we attempt to narrow
the lines that we would need to write to make the applications go, unit tests
included, then these required approximately

  * LiveView
    * 123 lines of Elixir
    * 13 lines of HTML template code
  * Angular
    * 274 lines of TypeScript
    * 31 lines of HTML template code

In this rough example, the LiveView implementation includes a resiliant backend
with dynamic, server-side rendered responses being generated in 380µs. For this,
we only wrote about **44% of the lines of code** and had a whole lot less to
worry about.

