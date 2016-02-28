# Generate lists \(gen-list\)

The `gen-list` step examines the input files and creates lists of topics, images, document properties, or other content. These lists are used by later steps in the pipeline. For example, one list includes all topics that make use of the conref attribute; only those files are processed during the conref stage of the build. This step is implemented in Java.

The result of this list is a set of several list files in the temporary directory, including dita.list and dita.xml.properties.

|List file property|List file|List property|Usage|
|------------------|---------|-------------|-----|
|canditopicsfile|`canditopics.list`|canditopicslist| |
|codereffile|`coderef.list`|codereflist|topics with coderef|
|conreffile|`conref.list`|conreflist|Documents that contains conref attribute that need to be resolved in preprocess.|
|conrefpushfile|`conrefpush.list`|conrefpushlist| |
|conreftargetsfile|`conreftargets.list`|conreftargetslist| |
|copytosourcefile|`copytosource.list`|copytosourcelist| |
|copytotarget2sourcemapfile|`copytotarget2sourcemap.list`|copytotarget2sourcemaplist| |
|flagimagefile|`flagimage.list`|flagimagelist| |
|fullditamapandtopicfile|`fullditamapandtopic.list`|fullditamapandtopiclist|All of the ditamap and topic files that are referenced during the transformation. These may be referenced by href or conref attributes.|
|fullditamapfile|`fullditamap.list`|fullditamaplist|All of the ditamap files in dita.list|
|fullditatopicfile|`fullditatopic.list`|fullditatopiclist|All of the topic files in dita.list|
|hrefditatopicfile|`hrefditatopic.list`|hrefditatopiclist|All of the topic files that are referenced with an href attribute|
|hreftargetsfile|`hreftargets.list`|hreftargetslist|link targets|
|htmlfile|`html.list`|htmllist|resource files|
|imagefile|`image.list`|imagelist|Images files that are referenced in the content|
|outditafilesfile|`outditafiles.list`|outditafileslist| |
|relflagimagefile|`relflagimage.list`|relflagimagelist| |
|resourceonlyfile|`resourceonly.list`|resourceonlylist| |
|skipchunkfile|`skipchunk.list`|skipchunklist| |
|subjectschemefile|`subjectscheme.list`|subjectschemelist| |
|subtargetsfile|`subtargets.list`|subtargetslist| |
|tempdirToinputmapdir.relative.value| | | |
|uplevels| | | |
|user.input.dir| | |Absolute input directory path|
|user.input.file.listfile| | |Input file list file|
|user.input.file| | |Input file path, relative to input directory|

