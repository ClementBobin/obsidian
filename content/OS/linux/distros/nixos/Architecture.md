# [Architecture](https://nixos.org/manual/nix/unstable/architecture/architecture#architecture)

This chapter describes how Nix works. It should help users understand why Nix behaves as it does, and it should help developers understand how to modify Nix and how to write similar tools.

## [Overview](https://nixos.org/manual/nix/unstable/architecture/architecture#overview)

Nix consists of [hierarchical layers](https://en.wikipedia.org/wiki/Multitier_architecture#Layers).

The following [concept map](https://en.wikipedia.org/wiki/Concept_map) shows its main components (rectangles), the objects they operate on (rounded rectangles), and their interactions (connecting phrases):

```
	.----------------.    
	| Nix expression |----------.    
	'----------------'          |            
			|              passed to            
			|                   | 
 +----------|-------------------|--------------------------------+ 
 | Nix      |                   V                                | 
 |          |      +-------------------------+                   | 
 |          |      | commmand line interface |------.            | 
 |          |      +-------------------------+      |            | 
 |          |                   |                   |            | 
 |    evaluated by            calls              manages         | 
 |          |                   |                   |            | 
 |          |                   V                   |            | 
 |          |         +--------------------+        |            | 
 |          '-------->| language evaluator |        |            | 
 |                    +--------------------+        |            | 
 |                              |                   |            | 
 |                           produces               |            | 
 |                              |                   V            | 
 | +----------------------------|------------------------------+ | 
 | | store                      |                              | | 
 | |            referenced by   V       builds                 | | 
 | | .-------------.      .------------.      .--------------. | | 
 | | | build input |----->| build plan |----->| build result | | | 
 | | '-------------'      '------------'      '--------------' | | 
 | +-------------------------------------------------|---------+ | 
 +---------------------------------------------------|-----------+  
					                                 |  
									            represented as
										             |
										             V
										      .---------------.                     
										      |     file      |                       
										      '---------------'
```

At the top is the [command line interface](https://nixos.org/manual/nix/unstable/command-ref/command-ref) that drives the underlying layers.

The [Nix language](https://nixos.org/manual/nix/unstable/language/) evaluator transforms Nix expressions into self-contained _build plans_, which are used to derive _build results_ from referenced _build inputs_.

The command line interface and Nix expressions are what users deal with most.

> **Note** The Nix language itself does not have a notion of _packages_ or _configurations_. As far as we are concerned here, the inputs and results of a build plan are just data.

Underlying the command line interface and the Nix language evaluator is the [Nix store](https://nixos.org/manual/nix/unstable/glossary#gloss-store), a mechanism to keep track of build plans, data, and references between them. It can also execute build plans to produce new data, which are made available to the operating system as files.

A build plan itself is a series of _build tasks_, together with their build inputs.

> **Important** A build task in Nix is called [derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-derivation).

Each build task has a special build input executed as _build instructions_ in order to perform the build. The result of a build task can be input to another build task.

The following [data flow diagram](https://en.wikipedia.org/wiki/Data-flow_diagram) shows a build plan for illustration. Build inputs used as instructions to a build task are marked accordingly:

```
+--------------------------------------------------------------------+ 
| build plan                                                         | 
|                                                                    | 
| .-------------.                                                    | 
| | build input |---------.                                          | 
| '-------------'         |                                          | 
|                    instructions                                    | 
|                         |                                          | 
|                         v                                          | 
| .-------------.    .----------.                                    | 
| | build input |-->( build task )-------.                           | 
| '-------------'    '----------'        |                           | 
|                                  instructions                      | 
|                                        |                           | 
|                                        v                           | 
| .-------------.                  .----------.     .--------------. | 
| | build input |---------.       ( build task )--->| build result | | 
| '-------------'         |        '----------'     '--------------' | 
|                    instructions        ^                           | 
|                         |              |                           | 
|                         v              |                           | 
| .-------------.    .----------.        |                           | 
| | build input |-->( build task )-------'                           | 
| '-------------'    '----------'                                    | 
|                         ^                                          | 
|                         |                                          | 
|                         |                                          | 
| .-------------.         |                                          | 
| | build input |---------'                                          | 
| '-------------'                                                    | 
|                                                                    | 
+--------------------------------------------------------------------+
```
# [File System Object](https://nixos.org/manual/nix/unstable/architecture/file-system-object#file-system-object)

Nix uses a simplified model of the file system, which consists of file system objects. Every file system object is one of the following:

- File
    
    - A possibly empty sequence of bytes for contents
    - A single boolean representing the [executable](https://en.m.wikipedia.org/wiki/File-system_permissions#Permissions) permission
- Directory
    
    Mapping of names to child file system objects
    
- [Symbolic link](https://en.m.wikipedia.org/wiki/Symbolic_link)
    
    An arbitrary string. Nix does not assign any semantics to symbolic links.
    

File system objects and their children form a tree. A bare file or symlink can be a root file system object.

Nix does not encode any other file system notions such as [hard links](https://en.m.wikipedia.org/wiki/Hard_link), [permissions](https://en.m.wikipedia.org/wiki/File-system_permissions), timestamps, or other metadata.

## [Examples of file system objects](https://nixos.org/manual/nix/unstable/architecture/file-system-object#examples-of-file-system-objects)

A plain file:

```
50 B, executable: false
```

An executable file:

```
122 KB, executable: true
```

A symlink:

```
-> /usr/bin/sh
```

A directory with contents:

```
├── bin 
│   └── hello: 35 KB, executable: true 
└── share     
	├── info     
	│   └── hello.info: 36 KB, executable: false     
	└── man         
		└── man1             
			└── hello.1.gz: 790 B, executable: false
```

A directory that contains a symlink and other directories:

```
├── bin -> share/go/bin 
├── nix-support/ 
└── share/
```