## Table of Contents

<table>
    <tr><td width=33% valign=top>

* [Hello world](#hello-world)
* [Running a project folder](#running-a-project-folder-with-several-files)
* [Comments](#comments)
* [Functions](#functions)
    * [Returning multiple values](#returning-multiple-values)
* [Symbol visibility](#symbol-visibility)
* [Variables](#variables)
* [Types](#types)
    * [Strings](#strings)
    * [Numbers](#numbers)
    * [Arrays](#arrays)
    * [Fixed size arrays](#fixed-size-arrays)
    * [Maps](#maps)
* [Module imports](#module-imports)
* [Statements & expressions](#statements--expressions)
    * [If](#if)
    * [In operator](#in-operator)
    * [For loop](#for-loop)
    * [Match](#match)
    * [Defer](#defer)
* [Structs](#structs)
    * [Embedded structs](#embedded-structs)
    * [Default field values](#default-field-values)
    * [Short struct literal syntax](#short-struct-initialization-syntax)
    * [Access modifiers](#access-modifiers)
    * [Methods](#methods)
* [Unions](#unions)

</td><td width=33% valign=top>

* [Functions 2](#functions-2)
    * [Pure functions by default](#pure-functions-by-default)
    * [Mutable arguments](#mutable-arguments)
    * [Variable number of arguments](#variable-number-of-arguments)
    * [Anonymous & high order functions](#anonymous--high-order-functions)
* [References](#references)
* [Constants](#constants)
* [Builtin functions](#builtin-functions)
* [Printing custom types](#printing-custom-types)
* [Modules](#modules)
    * [Module/package management](#modulepackage-management)
* [Types 2](#types-2)
    * [Interfaces](#interfaces)
    * [Enums](#enums)
    * [Sum types](#sum-types)
    * [Type aliases](#type-aliases)
    * [Option/Result types & error handling](#optionresult-types-and-error-handling)
* [Generics](#generics)
* [Concurrency](#concurrency)
    * [Spawning Concurrent Tasks](#spawning-concurrent-tasks)
    * [Channels](#channels)
    * [Shared Objects](#shared-objects)
* [Decoding JSON](#decoding-json)
* [Testing](#testing)
* [Memory management](#memory-management)
* [ORM](#orm)

</td><td valign=top>

* [Writing documentation](#writing-documentation)
* [Tools](#tools)
    * [v fmt](#v-fmt)
    * [Profiling](#profiling)
* [Advanced Topics](#advanced-topics)
    * [Dumping expressions at runtime](#dumping-expressions-at-runtime)
    * [Memory-unsafe code](#memory-unsafe-code)
    * [Structs with reference fields](#structs-with-reference-fields)
    * [sizeof and __offsetof](#sizeof-and-__offsetof)
    * [Calling C from V](#calling-c-from-v)
    * [Debugging](#debugging)
    * [Conditional compilation](#conditional-compilation)
    * [Compile time pseudo variables](#compile-time-pseudo-variables)
    * [Compile-time reflection](#compile-time-reflection)
    * [Limited operator overloading](#limited-operator-overloading)
    * [Inline assembly](#inline-assembly)
    * [Translating C to V](#translating-c-to-v)
    * [Hot code reloading](#hot-code-reloading)
    * [Cross compilation](#cross-compilation)
    * [Cross-platform shell scripts in V](#cross-platform-shell-scripts-in-v)
    * [Attributes](#attributes)
    * [Goto](#goto)
* [Appendices](#appendices)
    * [Keywords](#appendix-i-keywords)
    * [Operators](#appendix-ii-operators)

</td></tr>
</table>

<!--
NB: there are several special keywords, which you can put after the code fences for v:
compile, live, ignore, failcompile, oksyntax, badsyntax, wip, nofmt
For more details, do: `v check-md`
-->

