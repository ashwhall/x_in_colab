# X in Colab

Simple set of templates to facilitate the usage of languages other than Python in Google Colaboratory.

## Contents

- C in Colab (`c_in_colab.ipynb`)
- C++ in Colab (`c++_in_colab.ipynb`)
- Javascript in Colab (`js_in_colab.ipynb`)

## Usage
Upload the `.ipynb` files to Google Drive, then open them in Google Colaboratory.
Run the first cell, which sets up the cell magic to enable compilation/running of non-Python code. \
Then follow the language-specific instructions:


### C in Colab
This is a simple call out to `gcc` to perform compilation.

The cell containing your source code should begin with the following cell magic:
```
%%gcc
```
__To compile and run__:

- Just run the cell and interact with it as normal.



### C++ in Colab
The most complex of the three languages, this uses `g++` to perform separate compilation and linking, meaning that you can write multiple source and header files.

The first line of the cell containing the application entry-point (i.e. `int main(void) {...}`) must be:
```
%%gpp_main
```


Each header file must begin with the cell magic:
```
%%gpp_header --name <file_name>
```
where `<file_name>` is replaced with your desired identifier.


Each `.cpp` file (except the one with the entry-point) must begin with the cell magic:
```
%%gpp_source --name <file_name>
```
again, where `<file_name>` is replaced with your desired identifier.


__To compile and run__:

- Run each of the header cells before their corresponding source cells - this just writes the header file to disk.
- Run each of the source cells - this writes the source file to disk and compiles it into a `.o` object file.
- Run the main source cell - this writes the source file to disk, performs the final compilation and linking, then executes the program.


### Javascript in Colab
This is a simple call out to `node` to run the script.

The cell containing your source code should begin with the following cell magic:
```
%%node
```
__To run__:

- Just run the cell and interact with it as normal.



_All contributions welcome!_
