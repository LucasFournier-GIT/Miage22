# Projects

From week 4 to week 12 you will work (improve, extend) on one of these projects

## Microdown
Microdown is a better markdown. It can be used (integrated in the pillar document compilation chain) to produce slides, books, websites

### Bugfixing

https://github.com/pillar-markup/Microdown/

### Possible extensions
- Test de livres de Pillar a Microdown
- Detect URLs automatically without the `[]()` syntax
- Ecstatic: a static  web site renderer 
   - making foliage2 (foliage fully using microdown) [https://github.com/noha/foliage]()
- Designing a Blog
  - index + search	
- Extension to supporte citezen
  - [https://github.com/Ducasse/Citezen]()
  - Kozen is a little system to generate static web pages with citezen plugin [http://github.com/Ducasse/Citezen]()

- Math caching. 
   - Math expressions request a latex server that serves a form representing the math expression. 
   - It would nice to catch it locally.

- PlantUML like extension to support Design description in class comments
   -  https://plantuml.com/class-diagram
   - implementing some + placement

```
@startuml
Class01 <|-- Class02
Class03 *-- Class04
Class05 o-- Class06
Class07 .. Class08
Class09 -- Class10
@enduml
```


## Regis
A web app to register to conference https://github.com/ESUG/Regis

### Possible extensions
- Managing Talks
- More tests
- Changing back-ends
- Crash recovery

## Bloc (super adventurous)
Bloc is a new graphical library
- https://www.slideshare.net/esug/bloc-for-pharo-current-state-and-future-perspective
- [http://www.github.com/pharo-graphics/Bloc](http://www.github.com/pharo-graphics/Bloc)

## Iceberg
Iceberg is a powerful model and tool to manage code representation and git operations.

### Bugfixing

https://github.com/pharo-vcs/iceberg/issues

### Possible Extensions
- Cherry picking
- Optimization
- Tonel. Tonel is only able to parse full package


## Citezen 
Citezen is a library to manage scientific publications. It also support the generation of webpage, CVs...
- [http://github.com/Ducasse/Citezen]()

### Possible Extensions
- Revisit the bib model and visitors 
   - hierarchy for the fields (year, title,...) 
   - hierarchy for the kind of entry (chapter, PhD, Inproceedings, techreport)
- Merging, sorting, filtering bib files 
- Writing a new core for document 
   - study the existing one, xhtml, plain latex output are needed to generate either web sites or pdf documents
      - one idea could be generate microdown documents and use the document structure and visitor there instead of redoing everything.
      - we could have a kind of template in microdown and it would fill up the template with the section lists and we would get the document output done using microdown visitor. This way we do not reinvent the wheel in citezen. 
      - Check the files rmod.bib because it has some annotations. Check `CZStef new latex; html; bib ; generate`
   - need to be able to produce document with title, sections, and list of reference
   - should be able to control
      - order and selection of sections
      - order and selection of field (for example not showing DOI or note, or annotation)

 Here is an example of potential script
 ```
 query20162021
	"normally this is four years so we should stop in 2011 but there are fuzy so let us go until 2012"

	"self query20162021"

	| builder |
	builder := self new
		fileNamed: '/Users/ducasse/Workspace/SimpleFiles/LSEFiles/Bibliography/bib/rmod.bib';
		startingYear: 2017;
		endingYear: 2021;
		teamMembers: self teamFor20162021;
		keysOfBlackListedEntries: self blackListedEntries ;
		setFilteringOn;
		yourself.
	builder filter.
	^ builder 
```      
      
- Removing Phrase library, we should discuss if we need to replace it. It does not like. 
- Rules for Entries: the idea is to make sure that entries respect a set of validity rules and to fix the problems automatically
   - keys should follow a given pattern for example Duca00a
   - entires should all be formatted the same eg. InProceedings and not inproceedings Inproceedings...
   - entries should have at least the mandatory fields
   - each field should be separated by a comma
   - month should be the three first letters of a month in lowercase
   - More rules can be found in the ruby script testscript.rb
- Integration of Citezen into microdown eg. given a tag kzVisualization, a title and a description we should be able to generate from Microdown the following: 
   - a list of corresponding publications rendered in HTML
   - example http://stephane.ducasse.free.fr/TopicsBlockchain.html and its link from the main page http://stephane.ducasse.free.fr/
- Tool to edit bibentry and validate them
- Tool to look for entries. We could use Spec.

## Pharo Virtual Machine
The Pharo Virtual Machine is written in Pharo, transpiled to C.
It has an interpreter, a machine code compiler for ARM64, ARM32, x86, x64, and RISC-V.
- https://github.com/pharo-project/pharo-vm/

### Possible Tasks
- Review issues the Slang Pharo-to-C transpiler
   - Fix type inference issues
   - Fix code generation issues
   - remove warnings
- Review issues in the Pharo VM
   - remove duplicated code


## Roassal
Roassal3 is an agile visualization engine for Pharo.
- https://github.com/ObjectProfile/Roassal3/

### Possible Tasks
- Review charts: default colors, default ticks (see issues)
- Review layouts (see issues)
- writing tests
- writing parameterized tests

## Brea
A couple of years ago, I prototyped something between a static site generator and a decoupled/headless CMS, called Brea[1] and we did a lot of extensive workshops to teach how to use it. The site (in Spanish) for the workshops and documentation of Brea is made using Brea and you can see it at [2]. It tries to address the documentation needs of the local communities which use diverse places to write documentation (HegdeDoc, Internet Archive) and want to consolidate them in a unified place. We're now discussing to integrate Brea with TiddlyWikiPharo[3] as TiddlyWiki has become an integral part of our documentation practices and maybe we could try another take on it if we get enough resources for that.

- [1] [https://code.tupale.co/Offray/Brea]()
- [2] [https://mutabit.com/repos.fossil/indieweb/]()
- [3] [https://code.tupale.co/Offray/TiddlyWikiPharo/]()
