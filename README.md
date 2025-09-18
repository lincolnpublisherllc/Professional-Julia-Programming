Professional Julia Programming — Extracted Code (Chapter by Chapter)
What this is

This repo collects every code snippet I could reliably extract from the book Professional Julia Programming and organizes them chapter by chapter. The goal is to give you runnable examples, grouped the same way the book presents them.

114 snippets were extracted with a heuristic pass.

Each chapter has its own folder, for example chapter-01, chapter-02, and so on.

Files are numbered in the order they appear in the book, like chapter-03-002.jl.

If you spot a snippet that belongs with the one above or below it, let me know the file path and I can merge or split it.

Folder layout
Professional-Julia-Programming-Code/
  chapter-01/
    chapter-01-001.jl
    chapter-01-002.jl
    ...
  chapter-02/
    chapter-02-001.jl
    ...
  ...
  README.md  ← this document (if you save it)

File naming and extensions

.jl is the default for Julia code.

.yml for CI or YAML examples.

.sh for shell sessions or scripts with multiple commands.

.sql for database queries.

.json for JSON examples.

If you prefer everything in Julia only, you can convert non-Julia samples by copying the relevant commands into Julia run() calls or by using the ; shell mode in the Julia REPL.

How to run the Julia snippets

Open a terminal in the folder for the chapter you are studying.

Start Julia:

julia


Activate a temporary environment (keeps packages isolated while you test):

import Pkg
Pkg.activate(temp=true)


Add any required packages mentioned in the snippet. For example:

Pkg.add(["DataFrames", "HTTP", "JSON", "BenchmarkTools"])


Include and run:

include("chapter-03-002.jl")


Tips:

If a snippet is meant for the REPL rather than a script, you can paste it directly into the Julia REPL.

If a snippet references files, keep your working directory at the chapter folder unless noted in comments.

Reproducible setup

To make package versions consistent while you experiment, you can generate a Project and Manifest per chapter:

import Pkg
Pkg.activate(".")     # inside the chapter folder
Pkg.instantiate()     # creates Project.toml / Manifest.toml if they do not exist
# Add packages you need, for example:
Pkg.add(["DataFrames", "HTTP", "JSON", "BenchmarkTools"])


Check in Project.toml and Manifest.toml if you plan to share this code with a team.

Notes on non-Julia files

.yml samples show CI or workflow configuration. They are not meant to run in Julia. Use them as references for GitHub Actions or other CI tools.

.sh files show shell sessions. Either run them with bash or convert commands to Julia with run(\...`)or by using;` in the REPL.

.sql files can be executed in your SQL client or through a Julia DB package such as SQLite.jl or LibPQ.jl.

.json files are usually data payloads or configuration examples. Load them with JSON3.jl or JSON.jl.

Common packages you may need

Depending on the chapter, you might run into these:

DataFrames, CSV, JSON or JSON3

HTTP, Downloads

BenchmarkTools

Distributed

Database clients such as SQLite, LibPQ

Cloud or service SDKs mentioned in examples

Install with:

import Pkg
Pkg.add(["DataFrames", "CSV", "JSON", "HTTP", "BenchmarkTools"])

Troubleshooting

Missing package: Add it with Pkg.add("PackageName").

UndefVarError: Check if the snippet expects you to using PackageName first.

Path errors: Some examples assume relative paths. Run them from the matching chapter folder.

Version differences: If you are on a newer Julia or package version, a method name may have changed. Look up the package docs for the closest equivalent.

Conventions I used while extracting

Snippets were detected by indentation and common code keywords. This catches most code blocks but can occasionally pull in a command from prose or split a long example into two. If you point out any outliers, I will fix the file boundaries.

The order of files matches the order in the book within each chapter.

How to contribute changes

Edit the snippet in its chapter folder.

Add a short comment at the top describing your fix:

# Fix: updated HTTP.get usage for HTTP.jl v1.10


If you change dependencies, update Project.toml in that chapter folder.

License and fair use

These files are extracted examples for study and review. If you plan to publish them, confirm the original book’s license and any usage terms. When in doubt, attribute the source and link to the book.

Quick checklist

Open the folder for your chapter

Start Julia and activate an environment

Add required packages

include(...) the snippet

Adjust paths or data files if needed
