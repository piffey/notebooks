# Jupyter Lab Docker Setup

This should be everything needed to run the notebooks underneath and also work
as a decent-ish template for anyone trying to do the same.

## Adding Packages

When adding packages to the system that you want to "automagically" be installed
then add them to the requirements.txt and re-launch with:

`docker-compose up --build`

## Custom Settings

Save custom settings in the .jupyter folder as they will be automatically copied
in with the volume mounting. You can siphon these custom settings from the
"Advanced Settings" pane in Jupyter Lab, then put the files in the same place
they exist on the lab machine.

## Secret Storage

Don't put your secrets in notebooks you're saving. That's a horrible idea.
Instead use the system of the python-dotenv package where a .env file is loaded
into your Jupyter Notebooks automatically. See contained notebooks for an
example. There are certainly more elegant ways to do this with Vault or whatever
but nothing this simple.

## Clearing Sensitive Data In Notebooks

Before committing your notebooks, be careful about what data is contained within
them -- particularly if you are using a public repository. All of your work,
including any sensitive data during the course of your investigations, will be a
part of the notebooks. You can clear that using the following command:

`jupyter nbconvert --clear-output --inplace notebook.ipynb`

The `nbconvert` command also recognizes globbing so a simple `*.ipynb` can clear
all of your notebooks.

## Additional Data Sets

The docker-compose setup automatically loads in /data in the current working
directory to /data in the /data directory of the docker container. Therefore
if you need additional datasets (ex. historical ASN data for pyasn) place them
in that directory to have them become available.
