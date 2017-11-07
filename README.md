<p align="center">
  <img src="https://static.hoa-project.net/Image/Hoa.svg" alt="Hoa" width="250px" />
</p>

---

<p align="center">
  <a href="https://travis-ci.org/hoaproject/Heap"><img src="https://img.shields.io/travis/hoaproject/Heap/master.svg" alt="Build status" /></a>
  <a href="https://coveralls.io/github/hoaproject/Heap?branch=master"><img src="https://img.shields.io/coveralls/hoaproject/Heap/master.svg" alt="Code coverage" /></a>
  <a href="https://packagist.org/packages/hoa/heap"><img src="https://img.shields.io/packagist/dt/hoa/heap.svg" alt="Packagist" /></a>
  <a href="https://hoa-project.net/LICENSE"><img src="https://img.shields.io/packagist/l/hoa/heap.svg" alt="License" /></a>
</p>
<p align="center">
  Hoa is a <strong>modular</strong>, <strong>extensible</strong> and
  <strong>structured</strong> set of PHP libraries.<br />
  Moreover, Hoa aims at being a bridge between industrial and research worlds.
</p>

# Hoa\Heap

[![Help on IRC](https://img.shields.io/badge/help-%23hoaproject-ff0066.svg)](https://webchat.freenode.net/?channels=#hoaproject)
[![Help on Gitter](https://img.shields.io/badge/help-gitter-ff0066.svg)](https://gitter.im/hoaproject/central)
[![Documentation](https://img.shields.io/badge/documentation-hack_book-ff0066.svg)](https://central.hoa-project.net/Documentation/Library/Heap)
[![Board](https://img.shields.io/badge/organisation-board-ff0066.svg)](https://waffle.io/hoaproject/heap)

This library is an implementation of Heap data structure priority
queue. The order of heap depends on priority parameter. The
difference with [`SplHeap`](http://php.net/class.splheap) is that you
control the integer used to compare the order of items.  Giving you
the support of using item type *Scalar*, *Array*, *Object* or
*Closure*

`Hoa\Heap\Min` and `Hoa\Heap\Max` class interpret priority by
comparing priority numerically.  But you are free to implement your
own class if you want a different sort algorithm.

## Installation

With [Composer](https://getcomposer.org/), to include this library into
your dependencies, you need to
require [`hoa/heap`](https://packagist.org/packages/hoa/heap):

```sh
$ composer require hoa/heap '~0.0'
```

For more installation procedures, please read [the Source
page](https://hoa-project.net/Source.html).

## Testing

Before running the test suites, the development dependencies must be installed:

```sh
$ composer install
```

Then, to run all the test suites:

```sh
$ vendor/bin/hoa test:run
```

For more information, please read the [contributor
guide](https://hoa-project.net/Literature/Contributor/Guide.html).

## :information_source: Information

The default iteration process (through _foreach_ or _next_) do not
dequeue the Heap as `SplHeap` does.  If you want this behavior, you
must use Generator methods `top` or `pop` for iterate while removing
the item from a heap.

## Quick usage

As a quick overview, we propose to see two simple use cases.

### Min-Heap

Find a minimum item of a min-heap while retrieving priority value.

```php
$heap = new Hoa\Heap\Min();

$heap->insert('Laps 1', 15);
$heap->insert('Laps 2', 18);
$heap->insert('Laps 3', 8);

foreach($heap as $laps) {
    $priority = $heap->priority();
    echo " > $laps in $priority seconds\n";
}

/**
 * Will output:
 *     > Laps 3 in 8 seconds
 *     > Laps 1 in 15 seconds
 *     > Laps 2 in 18 seconds
 */
```

### Max-Heap with Generator

Find a maximum item of a max-heap and dequeue iteration (a.k.a. peek)

```php
// 1. Create an empty heap 
$heap = new Hoa\Heap\Max();

// 2. Adding new item with a priority integer to the heap
$heap->insert('Jane', 305);
$heap->insert('Paul', 344);
$heap->insert('Helen', 234);

var_dump($heap->count());

/**
 * Will output:
 *     int(3)
 */

// 3. dequeue the heap with item of maximum value
foreach($heap->top() as $name) {
    echo " > $name\n";
}

/**
 * Will output:
 *     > Paul
 *     > Jane
 *     > Helen
 */

// 4. Constat the heap is now empty after iteration on top generator
var_dump($heap->count());

/**
 * Will output:
 *     int(0)
 */
```

## Documentation

The
[hack book of `Hoa\Heap`](https://hoa-project.net/Literature/Hack/Heap.html) contains
detailed information about how to use this library and how it works.

To generate the documentation locally, execute the following commands:

```sh
$ composer require --dev hoa/devtools
$ vendor/bin/hoa devtools:documentation --open
```

More documentation can be found on the project's website:
[hoa-project.net](https://hoa-project.net/).

## Getting help

There are mainly two ways to get help:

  * On the [`#hoaproject`](https://webchat.freenode.net/?channels=#hoaproject)
    IRC channel,
  * On the forum at [users.hoa-project.net](https://users.hoa-project.net).

## Contribution

Do you want to contribute? Thanks! A detailed [contributor
guide](https://hoa-project.net/Literature/Contributor/Guide.html) explains
everything you need to know.

## License

Hoa is under the New BSD License (BSD-3-Clause). Please, see
[`LICENSE`](https://hoa-project.net/LICENSE) for details.

## Related project:s

There are no related project registered, Let us know by opening issue
if you use it and want be listed!
