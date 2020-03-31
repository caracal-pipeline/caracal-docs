# How to update the Caracal documentation

Make sure that you've got the latest `meerkathi` and `caracal_docs` in the same parent directory.

Go into the `caracal_docs` directory and type the following:
```
python make_caracal_docs.py
cd sphinx
make html
cd ../
```

Then commit and push your changes to this repository.

And you're done! The readthedocs page https://caracal.readthedocs.io will be updated automatically.
