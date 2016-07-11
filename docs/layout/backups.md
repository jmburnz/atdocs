## Backup Generated Layout Files

Each time you save the layout settings two files are generated for each template suggestion:

1. The `mytheme.info.yml` file is rewritten to add or remove regions.
2. The twig template for that page suggestions is saved to `mytheme/templates/generated/`

By default existing files are overwritten. You can check the option to "Enable backups"to save the existing files to `ytheme/backups`, in case you need to access or review previous info files and templates.



