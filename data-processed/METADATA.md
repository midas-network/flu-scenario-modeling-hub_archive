# Metadata file structure

Each model is required to have metadata in 
[yaml format](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html), 
e.g. [see this example metadata file](https://github.com/midas-network/flu-scenario-modeling-hub_archive/blob/master/data-processed/MyTeam-MyModel/metadata-MyTeam-MyModel.txt).

Please order the variables in this order.

## Required variables

### `team_name`

The name of your team that is less than 50 characters, no spaces. Will be displayed online.

### `model_name`

The name of your model that is less than 50 characters, no spaces. Will be displayed online.

### `model_abbr`

An abbreviated name for your model that is less than 30 alphanumeric characters. The model abbreviation must be in the format of `[team_abbr]-[model_abbr]`. where each of the `[team_abbr]` and `[model_abbr]` are text strings that are each less than 15 alphanumeric characters that do not include a hyphen or whitespace  Note that this is a uniquely identifying field in our system, so please choose this name carefully, as it may not be changed once defined. The model abbreviation will be displayed online.

### `model_contributors`

A list of all individuals involved in the forecasting effort,
affiliations, and email address. At least one contributor needs to have a valid email address. All email addresses provided will be added to an email distribution list for model contributors.

The syntax of this field should be

    name1 (affiliation) <user@address>, name2 (affiliation) <user2@address>, name3 (affiliation) <user3@addreaa>

### `website_url`

A url to a website that has additional data about your model.
We encourage teams to submit the most user-friendly version of your model, e.g. a dashboard, or similar, that displays your model scenarios.
If you have additionally a data repository where you store scenarios and other model code, please include that in your methods section below.
If you only have a more technical site, e.g. github repo, please include that link here.
Will be displayed online.

### `model_version`

A version number or date in YYYY-MM-DD format, to designate the version of the model used for submitted model projections. Will be displayed online.

### `methods`

A brief description of your methodology that is less than 200 characters. Will be displayed online.

### `license`

We encourage teams to submit as a "cc-by-4.0" to allow the broadest possible uses including private vaccine production
(which would be excluded by the "cc-by-nc-4.0" license).

Alternatively, add the name and URL of the license used, as in `cc-by-4.0, https://creativecommons.org/licenses/by/4.0/`
Or, add the value `LICENSE.txt`, if a LICENSE.txt file was added within the folder.

Will be displayed online.

## Optional

### `team_funding`

Acknowledgement of funding source, by name of funding agency, grant title, and grant number.

### `data_inputs`

A brief description of the data sources used to inform the model, using as much as possible standard terminology that includes a source name and the type of data, such as `CDC flusurvnet`, etc.

### `citation`

A bibliographic citation to a paper, website, or other object that people can go to to find out more about the model, in the style used by PubMed, as `"Smith J, Smith S, Smith C. MyModel is the best model. Nature. 2020 Aug. doi: 10.1038/s12345-678-90123-45."`


# Abstract file structure

For each model and round, an abstract file is in markdown format. A template of each round abstract is available in the folder [data-processed/Myteam-MyModel](https://github.com/midas-network/flu-scenario-modeling-hub_archive/tree/main/data-processed/MyTeam-MyModel). 

The same abstract model can be used: [2022-08-14-MyTeam-MyModel-abstract.md](https://github.com/midas-network/flu-scenario-modeling-hub_archive/tree/main/data-processed/MyTeam-MyModel/2022-08-14-MyTeam-MyModel-abstract.md)

The file should be named 
```
YYYY-MM-DD-team-model-abstract.md
```
