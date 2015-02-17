# Getopts clone with additional functionality

This is a backward compatible bash substitution for getopts.  
Getopts+ intends to offer additional functionality in the form of both handling long options, and enabling multiple parameter passing.  
The format is slightly different for long options and multiple parameters, but follows the same usage as getopts so as to be a standalone replacement for the original.  

# Usage

getopts+ handles most arguments in exactly the same way as getopts does.  
For example:  

`getopts fA:xt: var` is equivalent to `getopts+ fA:xt: var`  

Additionally, getopts+ offers multiple parameter parsing:  

`getopts+ fA::xt: var` specifies that `A` expects 2 parameters, while `t` expects one.  

getopts+ supports long options as well:  

`getopts+ fA-along-opt::,xt: var` specifies that `-A` has a long version `--along-opt`, both which require 2 parameters (note that dashes in the long opt are permitted).  

The format is as follows: `...[short][-long][:],...`  
An optional short version comes first followed by a dash `-` and the long version, then colons specifying the number of parameters, if any. If it is not the last argument, a comma ',' must follow. A long option is valid without a short version is well, for example `getopts+ fAxt:-long var` spepcifies the options `-f -A -x -t t_args --long` are handled.  

