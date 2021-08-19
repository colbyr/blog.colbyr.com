## "b" is for "bindings"

I'm [learning  Erlang](https://learnyousomeerlang.com/). It's been fun! The Erlang shell is a great environment for poking around. You get there by typing `erl` into the terminal.

```erl
Erlang/OTP 24 [erts-12.0.3] [source] [64-bit] [smp:16:16] [ds:16:16:10] [async-threads:1] [jit] [dtrace]

Eshell V12.0.3  (abort with ^G)
1>
```

It might feel familiar if you've used the console in a web browser or a REPL in another language.  [Like the browser console](https://css-tricks.com/can-copy-console/),  Erlang's shell environment includes handy shortcuts for shell-related activities. These are their stories.

## "b" as in "bindings"

Variables in Erlang are immutable. You can't change 'em. I knew that going in, but it often trips me up in the shell.

```
1> One = 1.
1
2> Two = One + One.
2
3> One = 2.
** exception error: no match of right hand side value 2
```

Once you define a variable, you can't set it again. Immutable. Right. But sometimes, in a long shell session, I clear my screen or just forgot what variables I set.

Try `b/0`. It prints out all the variables defined in the current session along with their assigned values.

```
4> b().
One = 1
Two = 2
ok
```

## "f" as in "forget"

Even better, `f/1` will _unbind_ a variable you want to reuse.

```
12> b().
One = 1
Two = 2
ok
13> f(One).
ok
14> One = 2.
2
```

And if you need a clean slate, `f/0` removes _all_ variable bindings in the session.

```
16> b().
One = 2
Two = 2
ok
17> f().
ok
18> b().
ok
```

That's all for now. Check out the rest of  [the rest of the series](https://blog.colbyr.com/series/e-as-in-eshell) for more shell commands, or get straight into [the docs](https://erlang.org/doc/man/shell.html#shell-commands).

