
```ebnf
prg              = prgHeader varDefs { funcDef } "begin" statementSeq "end" "."

prgHeader        = "program" identifier ";"

varDefs          = [ "var" varSeq { varSeq } ]
varSeq           = identifier { "," identifier } ":" type ";"
type             = "integer" | "string"

funcDef          = "function" identifier "(" [paramSeq] ")" ":" type ";" varDefs "begin" statementSeq returnStmt "end" ";"
paramSeq         = identifier ":" type { "," identifier ":" type }
returnStmt       = "return" operand ";"

statementSeq     = { ( simpleAssignment | complexAssignment | funcCall ) ";" }

simpleAssignment = identifier ":=" operand
complexAssignment= identifier ":=" operand mathOp operand

funcCall         = identifier "(" [argumentSeq] ")"
argumentSeq      = operand { "," operand }

operand          = identifier | number | funcCall

mathOp           = "+" | "-"
```
