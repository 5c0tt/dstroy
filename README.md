08.08.2015 — 07:34:10 PM -0700  
Scott Haneda [@scotthaneda](https://twitter.com/scotthaneda)

#dstroy - a simple command line helper for DS.Store files and keeping DropBox from getting bloated

Right now, I don't have time to write docs, the code is relatively self explanatory, and a huge hack, which will get cleaned up over time.

The general logic is:
app_name dir_path

When app_name is called, it takes in dir_path and checks it to make sure it is a valid path, which is not much of a test, just making sure it is there is all I am doing.

Then `find` is called, which located all files of type -f and name of .DS_Store, and deletes all those recursively from dir_path.  I have -i from the rm command enabled, so you have to "y" every deletion for the time being.  Ideally I would move them to the trash, but couldn't figure out how to do it.  I will make a function and it should be easy to pass that in.

Once find has all the files, and the DS_Store files are deleted, I run one more find, to locate all "large" files.  With my droppings app, DropBox being stingy, until I build my own cloud system, I need to make sure I remember that I put up a 1GB disk image and need to take it down, this helps that mess, and the mess of 1000's of jpg's etc that build up.

A sorted list based on file size and a path to the file is created in /tmp and then opened in [Textmate](https://macromates.com/)