# SIMBAD-DOCS

This is shared documentation repository for readthedocs builds.
Live documentation: [link](https://simbad-docs.readthedocs.io)
Readthedocs builds: [link](https://readthedocs.org/projects/simbad-docs/builds/)

### Triggering documentation build
Builds are triggered automatically after new master commits. To update documentation for components of Simbad project
it is necessary to update submodules
```
git submodule foreach git pull origin master
git add .
git commit -m "Update submodules"
git push
```
### Writing and building documentation locally
Documentation is build using Sphinx, written in markdown using recomonnmark plugin. Building html documentation: 
```
make html
```
The docs structure however, is build using .rst files - all markdown files from each project must be attached to toctree
in some index.rst file. You can attach files in main index.rst:
```
Simbad Client
=============
.. toctree::
   :maxdepth: 3

   simbad-client/README
   simbad-client/usage-docs/index

```
Or create separate index.rst file for subproject, and attach all of the markdown files there:
In source/index.rst file:
```
Simbad Host
=============
.. toctree::
   :maxdepth: 3

   simbad-host-link/docs/index

```
In source/simbad-host-link/docs/index.rst file:
```
.. toctree::
   :maxdepth: 2
   
   file
```

