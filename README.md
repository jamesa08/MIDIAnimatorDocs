# MIDIAnimator documentation

Read the docs here: https://midianimatordocs.readthedocs.io/

To build:

1. Clone the repository `git clone https://github.com/imacj/MIDIAnimatorDocs.git`.
2. Run `pip install -r docs/requirements.txt`.
3. Run `cd docs && make clean && make html` in the repository directory.
4. Open `index.html` or run `cd build/html/ && open index.html` (for Mac users).

Note: Instead of reStructuredText markdown files, we are using MyST markdown files. For some basic information on MyST markdown, visit https://myst-parser.readthedocs.io/en/v0.15.1/sphinx/intro.html.

**Please open a PR if you want to make changes to the docs.**

<!--

Useful commands:

for building (in docs dir)
make clean && make html

for opening built html and going back to docs dir
cd build/html/ && open index.html && cd ../../

-->
