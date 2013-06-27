# Solve
[![Gem Version](https://badge.fury.io/rb/solve.png)](http://badge.fury.io/rb/solve)
[![Build Status](https://secure.travis-ci.org/RiotGames/solve.png?branch=master)](http://travis-ci.org/RiotGames/solve)
[![Dependency Status](https://gemnasium.com/RiotGames/solve.png?travis)](https://gemnasium.com/RiotGames/solve)

A Ruby versioning constraint solver implementing [Semantic Versioning 2.0.0](http://semver.org).

## Installation

    $ gem install solve

## Usage

Create a new graph

    graph = Graph.new

Add an artifact to the graph

    graph.artifacts("nginx", "1.0.0")

Now add another artifact that has a dependency

    graph.artifacts("mysql", "1.2.4-alpha.1").depends("openssl", "~> 1.0.0")

Dependencies can be chained, too

    graph.artifacts("ntp", "1.0.0").depends("build-essential").depends("yum")

And now solve the graph with some demands

    Solve.it!(graph, ['nginx', '>= 0.100.0'])

### Removing an artifact, or dependency from the graph

    graph.artifacts("nginx", "1.0.0").delete

    artifact.dependencies("nginx", "~> 1.0.0").delete

## Authors

* [Jamie Winsor](https://github.com/reset) (<reset@riotgames.com>)
* [Andrew Garson](andrewGarson) (<agarson@riotgames.com>)
* [Thibaud Guillaume-Gentil](https://github.com/thibaudgg) ([@thibaudgg](http://twitter.com/thibaudgg))
