# Introduction #

Pyew supports plugins in the form of Python classes. A Pyew plugin can be used in either interactive or batch mode. In batch mode, typically, the plugin returns the corresponding result and in interactive mode shows the results.

# Example plugin #

The following is a dummy plugin you may use as a template for your own plugins:

```
def example(pyew):
  print "Hello world!"

functions = {"hello":example}
```

Save it as, for example, hello.py and place this file in the plugins directory. Now, you can issue in Pyew the command "hello" to see the message "Hello World!".

To add support for batch mode, you can change the current plugin in one of the following ways:

**Mode 1**
```
def example(pyew):
  if pyew.batch:
    return "Hello World!"
  else:
    print "Hello World!"
```

**Mode 2**
```
def example(pyew, doprint=True):
  if doprint:
    print "Hello World!"
  else:
    return "Hello World!"
```

The 2nd mode is the prefered one.

# Plugins List #

As of 2010-01, the following is the list of plugins distributed with Pyew:

# File structure #

## ole2 ##

Print the OLE2 structure of the currently opened file or buffer. Uses [OleFileIO\_PL by Philippe Lagadec](http://www.decalage.info/python/olefileio).

## packer ##

Try to detect the compiler and/or packer's signature. Uses [PEUtils by Ero Carrera](http://code.google.com/p/pefile/source/browse/trunk/peutils.py). A UserDB.txt file with ~4445 signatures is distributed with Pyew.

In interactive mode, the plugin returns a list with every matched signature.

# Graphs #

## cgraph ##

Shows the callgraph of the current program with [xdot.py by Jose Fonseca](http://code.google.com/p/jrfonseca/wiki/XDot).

In batch mode, the plugin returns a DOT buffer.

## binvi ##

Show an image representing the current opened file or buffer. Requires [Python Imaging Library](http://www.pythonware.com/products/pil/).

# URL management #

## url ##

Search URLs in the current file or buffer. In batch mode, the plugin returns a list with every detected URL.

## chkbad ##

Search URLs in the current file or buffer using the 'url' plugin and check if any of the URLs is known to be bad using the malware's URL list distributed by [MalwarePatrol](http://www.malware.com.br/lists.shtml).

## chkurl ##

Search URLs in the current file or buffer using the 'url' plugin and check if the URL is still alive or not.

# External Services #

## vt ##

Search the hash of the current file or buffer using the [VirusTotal](http://www.virustotal.com) search hash utility and prints the AV detection results. Currently, the plugin doesn't support uploading the current sample or buffer. This feature will be added soon.

## threat ##

Open in a browser the behavior's report generated by ThreatExpert. The report may or may not exists. The plugin doesn't support uploading the current file or buffer.

# PDF Support #

## pdfview ##

Show decoded streams data in a GUI.

## pdfvi ##

Print decoded streams data (text mode).

## pdfilter ##

Get information about the streams. Show a list of the streams with filters applied to them.

## pdfstream ##

Show the list of streams.

## pdf ##

Show general information about the PDF.

## pdfobj ##

Show the PDF's object list.

## pdfso ##

Seek to one specified object.

## pdfss ##

Seek to one specified stream.

# Other plugins #

## antivm ##

Search for common antivm tricks. Subject to be replaced soon.

## sc ##

Search for shellcodes in the current file or buffer using [LibEmu](http://libemu.carnivore.it/). **Subject to be removed soon**.