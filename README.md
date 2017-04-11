# UBL_thesis_template
This close-to-empty project provides the minimal LaTeX files architecture to
write a thesis with:

- [x] Approved first cover,
- [x] Optional epigraph (quotes at a chapter beginning),
- [x] Optional minitoc (small table of content at a chapter beginning).



# Compilation
To compile this project it is advised to use the command:

`pdflatex -output-directory ./build thesis.tex && mv build/thesis.pdf .`

This command keeps the root directory clean since all temporary files are put
into the `build` directory. Of course, this command is usually needed twice in
order to correctly produce hyper-references. As for bibliographic references the
command `bibtex` is also needed.


## Auto-compilation
On a side note, I suggest to use `inotifywait` command, from the Linux package
`inotify-tools`, and a script that will automatically compile the document each
time a `*.tex` file is saved. This scripts ends by printing a green-message if
all references are valid or a red-message with the list of missing references.


## Docker
I also use a Docker image that embeds all LaTeX packages to ease compilations
from different computers effortlessly. The Docker image I use embeds
[minted package](https://github.com/gpoore/minted) that provides great syntax
coloration for source code. The Dockerfile is in the `Docker` directory and can
be built, once in the `Docker` directory, with the command
`docker build -t pdflatex .`. This image also provide `bibtex` command.
Then make sure your Docker daemon is running, and execute `auto-compile.sh`
to automatically compile your thesis.
