# Rust Python Package Example
Example of how to make a python package out of a Rust library implementation, using the pyo3 library.

To make python package:
```shell
python3 setup.py sdist
```

To install as a python package you will need to have the Rust toolchain installed, to compile the library for your architecture.

Install Rust as recommended by https://rustup.rs/.

It was required to have Rust on nightly when I did this (when rust nightly was at 1.35, and stable on 1.33) so if it still is enable nightly with
```shell
rustup default nightly
```

Also you will need to install the required python3 modules, but just do that with pip3 if you get an error about 'no module found'.

Then run setup.py to install the package

```shell
python3 setup.py install --user
```

Finally import the module in a python script like a normal library, and run functions with
```shell
from rust_python_package_example import module_example

module_example.print_info("Hello World from Rust!")
```

### Troubleshooting
When I did this the first time on Fedora 29 I encountered a problem where cargo or rust couldn't find the python interpreter because it was looking at 'python' rather than 'python3', so to fix it I just made a symbolic link in /usr/bin/. If you already have Python 2 installed and there already exists a file named python there this will be problematic, but to do it create a symlink with:
```shell
sudo ln -s /usr/bin/python3 /usr/bin/python
```

You should probably delete the link after to avoid problems with other packages.

