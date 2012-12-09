# Clojure Notes

## Startup

    // bare bones repl
    java -cp clojure.jar clojure.main --repl		

    // get help
    java -cp clojure.jar clojure.main --help

    // use the homebrew stratup script
    clj

    // use rlwarp (via homebrew) for command history and arrow keys
    rlwarp clj

    // run a script
    clj scriptName.clj

    // execute code from the command line
    // usefull for compilation
    clj -e "(println (+ 1 1))"

## Compilation

    // Use the compile function
    // NOTE: clojure code must be in the proper folder structure
    //       in the example /mypkg/hello.clj must be in the current directory
    // NOTE: /classes must exist in the directory where this command is run
    java -cp clojure.jar:. clojure.main -e "(compile 'mypkg.hello)"

    // Compile with a main method
    // a :gen-classes form and a funtion named "-main" must be present as follows
    (ns mypkg.hello
	(:gen-class))

	(defn -main 
		[] 
		(println "Hello from clojure main!"))

	// Compile as above and then run with
	java -cp clojure.jar:classes/ mypkg.hello
