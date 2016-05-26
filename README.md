# VCS Repository Management for Go

Manage repos in varying version control systems with ease through a common
interface.

[![Build Status](https://travis-ci.org/Masterminds/vcs.svg)](https://travis-ci.org/Masterminds/vcs) [![GoDoc](https://godoc.org/github.com/Masterminds/vcs?status.png)](https://godoc.org/github.com/Masterminds/vcs) [![Go Report Card](http://goreportcard.com/badge/Masterminds/vcs)](http://goreportcard.com/report/Masterminds/vcs)

## Quick Usage

Quick usage:

	remote := "https://github.com/Masterminds/vcs"
    local, _ := ioutil.TempDir("", "go-vcs")
    repo, err := NewRepo(remote, local)
        
    remote := "svn://git.oschina.net/goops/FirstProject"
    // local, _ := ioutil.TempDir("", "go-vcs")
    local := dir + path + "md"
    args := []string{"--username", "xxx@gmail.com", "--password", "xxxxxx"}
    repo, err := vcs.NewSvnRepo(remote, local, args...)
    if err != nil {
        log.Fatalln(err)
    }
    log.Println(repo.Get())

In this case `NewRepo` will detect the VCS is Git and return a `GitRepo`. All of
the repos implement the `Repo` interface with a common set of features between
them.

## Supported VCS

Git, SVN, Bazaar (Bzr), and Mercurial (Hg) are currently supported. They each
have their own type (e.g., `GitRepo`) that follow a simple naming pattern. Each
type implements the `Repo` interface and has a constructor (e.g., `NewGitRepo`).
The constructors have the same signature as `NewRepo`.

## Features

- Clone or checkout a repository depending on the version control system.
- Pull updates to a repository.
- Get the currently checked out commit id.
- Checkout a commit id, branch, or tag (depending on the availability in the VCS).
- Get a list of tags and branches in the VCS.
- Check if a string value is a valid reference within the VCS.
- More...

For more details see [the documentation](https://godoc.org/github.com/Masterminds/vcs).

## Motivation

The package `golang.org/x/tools/go/vcs` provides some valuable functionality
for working with packages in repositories in varying source control management
systems. That package, while useful and well tested, is designed with a specific
purpose in mind. Our uses went beyond the scope of that package. To implement
our scope we built a package that went beyond the functionality and scope
of `golang.org/x/tools/go/vcs`.
