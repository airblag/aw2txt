# aw2txt

aw2txt is a *dirty* shell script extracting text from a Applixware Words document (.aw) and trying to produce a text output from it.

It was tested with simple documents produced by Applixware 4.42 (I guess from 1997). Since the only existing converter from abiword doesn't seem to work, I tought it may help someone else to get rid of old Applix documents.

## Dependencies

should work on any Linux distribution...

- GNU sed (not sure if -z is supported in other versions)
- (GNU) awk (i should have done it with sed but I was lazy to find out how to do it)
- bash (not sure if I'm using anything bash specific...)

## Example

An example Applix Words document created with Applixware 4.42 (1021.500) is in the repository as test/Applix_wikipedia.aw

```
$ ./aw2txt test/Applix_wikipedia.aw 
Applix

From Wikipedia, the free encyclopedia
Applix Inc. Industry 	Computer Software
Fate 	Acquired by Cognos, October 25, 2007; Acquired by IBM, January 31, 2008
Founded 	1983
Headquarters 	Westborough, Massachusetts, USA
Products 	

    Applix TM1
    Applix WebExecutive Viewer
    Business Analytics Platform

Owner 	IBM
Website 	www-01.ibm.com/software/analytics/cognos/

Applix Inc. was a computer software company founded in 1983[1] based in Westborough, Massachusetts that published Applix TM1, a multi-dimensional online analytical processing (MOLAP) database server, and related presentation tools, including Applix Web and Applix Executive Viewer. Together, Applix TM1, Applix Web and Applix Executive Viewer were the three core components of the Applix Business Analytics Platform. (Executive Viewer was subsequently discontinued by IBM.[2])

On October 25, 2007, Applix was acquired by Cognos. Cognos rebranded all Applix products under its name following the acquisition. On January 31, 2008, Cognos was itself acquired by IBM.

Prior to OLAP industry consolidation in 2007, Applix was the purest OLAP vendor among publicly-traded independent business intelligence vendors, and had the greatest growth rate.[3][4] TM1 is now marketed as IBM Cognos TM1; version 10.2 became publicly available on September 13, 2013.
Products and technology

Applix TM1 is enterprise planning software used for collaborative planning, budgeting and forecasting, as well as analytical and reporting applications. Data in TM1 is stored and represented as multidimensional cubes, with data being stored at the "leaf" level. Computations on the leaf data are performed in real-time (for example, to aggregate numbers up a dimensional hierarchy). IBM Cognos TM1 also includes a data orchestration environment for accessing external data and systems, as well as capabilities designed for common business planning and budgeting requirements (e.g. workflow, top-down adjustments).
```

## Limitations

- This script tries to extract text from Applix tags ```<T "Text content" >``` and replaces tags ```<P.* ``` with new lines.
- It also translates a few encoded extended characters (öäüßéèçê [...] to the UTF-8 equivalent).
- Anything else is hopefully ignored. 
- Complex documents might produce unexpected output.

