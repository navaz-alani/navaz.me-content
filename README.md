# Content for `navaz.me`

This repository contains the code that is served on my
[personal website](https://navaz.me/content).

The content is stored in categories. Each category is a directory in the root
of this repository, conforming to the following name format
`<category_code>:<category_name>`. Directories which do not follow this format
are simply ignored.

Inside each category, there are documents to be served. These documents are
organized by file/content type. This is specified by directories named like:
`<resource_type_code>:<file_extension>:<resource_type_name>`. Directories which
do not conform to this name convention are ignored.

Finally, resources are located in each content type directory. There is one
reserved file, called `enum.txt` in each of these directories which provides
meta-data about the resources within that directory. If a file is listed in the
`enum.txt` file, exists in the directory and has the right extension it will be
served.

## TODO

The server which parses and serves this content is located in the backend code
for my personal website. This was my first attempt at a content delivery system
and I have, since then, come up with many improvements that I can make.

__Improvements__:

* This design was created with some policy implementations. This should be
  avoided. All policy should be implemented at the server side.
* A better format for the `enum.txt` meta data files. I do not support
  meta-data being included in files themselves because any changes would need
  the files themselves to be edited. With this approach, it is easier to manage
  and has computational benefits too (arguably, to some extent).
