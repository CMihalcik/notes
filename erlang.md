# Startup
    erl 
launches a shell, which is a vm, which is a node

# Shut down a shell
    Control+\
or
    halt()

# Shut down a shell cleanly
    init:stop()

# File system nav
```
cd().
ls().
pwd().
```

# Compile
    c("some file name.erl").


# Run a function 
The format is namespace:functionName(args).
    namespace:function().

# Erlang processes are isolated

# Functions
- start with an ->
- end with a .
- statements are seperated by a ,
- statements with multiple clauses seperate them with a ;
- statements with multiple clauses do not put anything after the last clause

# Clear shell variables
    f().

# Pid ! is fire and forget
Is this what they call naked banging?

# Loading an erl
- code is loaded from the codepath, .erl files in the cd of the repl will be found automatically

# Running a function from a module
- can be done by entering the following:
	module:exportedFunctionName().

# Lists active erl nodes
    nodes().

# RPC
- remote pricedure call, run something on a remote node

# spawn()
- will start a new processs, optionally on a remote node

# List comprehension
    [X || X <- lists:seq(1,10)].
produces [1,2,3,4,5,6,7,8,9,10]
    [X*2 || X <- lists:seq(1,10)].
produces [1,2,3,4,5,6,7,8,9,10]

# Command Line docs:
http://erlang.org/doc/man/erl.html

# API Docs
http://erldocs.com/R15B/

# Opening new nodes
From the terminal:
```erl -sname someNodeName```
- this will launch a node with a repl and will report it's 'name' as someNodeName@hostname


# Detecting other Nodes
    nodes().
- will probably return an empty list
- []

# Connecting to other nodes
    net_adm:ping(nodeName@hostName).
- should respond with 
	pong
- if there are special characters in the name you'll need to warp it in ticks, tech. the problem is that this isn't a valid atom name
    net_adm:ping('dog@host').
- might have a problem connecting from sublime because it doesn't have a name
- fixed this by updating /Users/chrismihalcik/Library/Application Support/Sublime Text 2/Packages/SublimeREPL/config/Erlang/Main.sublime-menu

# Load a module (a compiled module) on all connected nodes
    nl(modulename).

#Start a module on a remote node
    spawn('nodeName@hostname', module, function, args).
e.g.
    spawn('dog@Chriss-MacBook-Pro', atm, stop, []).
- will return the erlang pid of the process

# Stop all atms on connected nodes (does not include the current node)
    [spawn(X, atm, stop, []) || X <- nodes()].

# Stop all atms on connected nodes including the current node)
   [spawn(X, atm, stop, []) || X <- nodes()++[node()]].





