ForeachParallel-Task for Phing
==============================
![project status](http://stillmaintained.com/mkrauser/roundcube_fileapi_attachments.png)

## Maintainer Contact

Matthias Krauser
mail:    <matthias@krauser.eu>
twitter: [@mat_krauser](https://twitter.com/mat_krauser) 

## Changelog

### 1.0.0 (2014-10-27)
* initial release

## Documentation

The foreach-parallel-task for phing behaves exactly like the normal foreach-task. From the documentation of the [foreach-task](http://www.phing.info/docs/guide/trunk/apbs16.html):

*The foreach task iterates over a list, a list of filesets, or both. If both, list and filesets, are specified, the list will be evaluated first. Nested filesets are evaluated in the order they appear in the task.*

The only difference is, that the iterations are not executed sequentially but parallel. It like a foreach-version of phing's [ParallelTask](http://www.phing.info/docs/guide/trunk/apcs43.html). 

This only works on *nix machines with pcntl-extension installed. If the requirements are not fullfilled, the foreach-parallel-task will behave like a regular foreach-task.

## Installation

The suggested installation method is via [composer](https://getcomposer.org/):

```sh
php composer.phar require "doctrine/instantiator:~1.0.3"
```

## Usage

* Load the task in your phing build-file
```xml
<taskdef name="foreach_parallel" classname="MaK\Phing\Task\ForeachParallelTask" />
```

* Call the task:
  The syntax is exactly the same as the original task. The only difference is the optional `threadCount`-Attribute, to specify the maximum number of threads / processes to use. If not specified, the library will try to guess the best number.
```xml
<foreach_parallel list="..." param="some_param" target="target-task" threadCount="4"/>
```

## Credits

This library task was heavily inspired by ParallelTask from  Michiel Rook (<mrook@php.net>), which is part of the Phing-Core. 