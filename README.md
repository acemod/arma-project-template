# Arma3 AddOn Project template

A project template for Arma3 AddOn projects using the ACE3 framework. This template is based off the ACE3 project structure.

### Development Environment

See the [ACE3 documentation](http://ace3mod.com/wiki/development/setting-up-the-development-environment.html) on setting up your development environment

### Usage

Search and replace all mentions of the following:
```
proj_templ by {your_prefix}
```

```
PROJ_TEMPL by {PROJ_TEMPL}
```
Note that both lower and upper case are necessary. Once done, replace the logo (`logo_proj_templ_ca.paa`) by your own. Keep the same aspect ratio and file extension (`.paa`). This is important for good results in game. Also remember to rename the logo file to `logo_{your_prefix}_ca.paa`.

##### Example:

```
proj_templ by acex
```

```
PROJ_TEMPL by ACEX
```

### Using CI

This template comes with some basic scripts to validate and enforce parts of the ACE3 coding guidelines. You can find those scripts in the tools directory.

- sqf_validator.py - checks all .sqf files in the addons directory and checks for missing brackets, missing semi-colons and tab usage.
- config_style_checker.py - checks all .hpp and .cpp files in the addons directory and checks for missing brackets and tabs.

For more information on the guidelines, see ACE3 coding guidelines.

You can use these scripts in combination with CI - if you are on GitHub and use Travis-CI, here is an example:

```yml
language: python
python:
- '3.4'
script:
- python3 tools/sqf_validator.py
- python3 tools/config_style_checker.py
```

### Adding new components

Adding a new component to your project is done by copying the example component directory and renaming it. Follow these steps:

- Copy the blank example component directory into the addons directory
- Rename the component directory name (blank -> {your component name})
- Do a search and replace of `blank` by `your component name`. Take care to preserve case sensitivity.
- Ensure that the required AddOns in the `config.cpp` file inside your new component are set correctly. You will need at least a requirement to the main component of your project. Any other modifications that your component depends on will also need to be listed here, including your own components that you depend upon.
- Start work on your component.
