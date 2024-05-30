# Virtual Environment Manager

This simple script makes creating and managing named virtual environments in Python super easy! It also adds a new type of environment style for Node that allows you to install one set of packages in one place and utilize them anywhere!

Python venv's work as expected, can even utilize a special alias called `de` that is shorthand for the `deactivate` command made with each Python venv.

Node venv's are a bit complex as they require some hands-on pathing to use the packages in that area. One way that works is to interpolate the path to the node_modules folder into the `require()` function. Dynamic import can be a bit strange as even if you pass `NODE_PATH` the paths, it won't look for the module in the folder at all. This is still a work in progress as not all packages that have legacy support for CommonJS modules work as expected. This can usually mean that even dynamic import() won't work. Great example of this issue is attempting to use axios via `require`. Axios requires that you import it via ESM syntax, but to do so you need to enable ESM syntax upon executing the file. This is not ideal as not all packages support ESM syntax yet and using both ESM and CommonJS syntax can lead to some unexpected outcomes. ESM also does not take into account the `NODE_PATH` variable or allow you to look at absolute paths.

Usage is fairly straight forward, you specify the type of environment you would like to make with `-j` or `-p`, followed by the name of the environment you are creating. Alternatively, you can specify `-d` to delete to remove the environment instead of creating it. Optionally add `-V` for verbose logging.

To create and adjust system-wide venvs, prepend the command with `sudo` to point to the system-wide variant. This is a work in progress and integration for script and app generators is also work in progress.
