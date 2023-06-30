# 42--minishell-intra-version

Syntax Rules :

Readline's output (ie the user's input) is here seen as a complex command.
A complex command is composed of pipelines, separated by control operators (and ("&&), or "||", end of the command (ie a ";")).
Parenthesis can be used to specifiy the order of priority. 
A pipeline consists of simple commands, separated by pipes.
A simple command consists of a succession of in-and-out redirections, and words (later interpreted as a command name and arguments/options).
Example : 
    - Simple commands : 
        - < in1 <in2 cmd_name cmd_arg1 cmd_arg2 cmd_arg3 >out1 >out2 >out3
        - cmd_name <in1<in2 cmd_arg1 cmd_arg2 >out1 >> out2 cmd_arg3 <in3 >out3
        In summary, the redirection operands and command name/arguments' order does not matter.
        Differentiating the two of them is done by parsing the simple command : 
        The token following an in-out redirection operator is always considered the associated in-out-file. 
        The remaining <word>'s tokens are interpreted as the command's name and arguments.
    - Pipeline :
        - simple_cmd1 | simple_cmd2 | ... | simple_cmd7
    - Complex command :
        - pipeline1 && (simple_cmd1 || pipeline2).
            Here, if pipeline1 is correctly exectued, what follows in the parentheses won't be executed.
            On the other hands, if there were no parentheses, the pipeline2 would have been executed.

In-out redirections (<, <<, >, >>)
    - 
    - 
    -

Pipes :

And-or control operators :




Tricky commands :
    - A command consisting only of the expansion of a variable that does not exist ($DOESNOTEXIST) should give the prompt back
    - $"" should be assessed as the empty string, and "minishell : ` ' : command not found" should be printed
