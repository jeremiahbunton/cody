---
title: cb init
reference: true
---

## Usage

    cb init

## Description

Set up initial .codebuild files.

## Examples

    cb init # infers the name from the parent folder
    cb init my-project # set the name

## Type Option

The type option is useful to generate subfolder under .codebuild that contain another codebuild project.  Example:

    cb init --type unit

Thi generates the cb files under the `.codebuild/unit` folder.

    .codebuild
    └── unit
        ├── buildspec.yml
        ├── project.rb
        ├── role.rb
        └── schedule.rb

To tell the codebuild tool to use these files, you specify the `--type` option as a part of the other commands. Examples:

    cb deploy --type unit
    cb start --type unit

## Structure

So if you need multiple CodeBuild projects that perform different tasks but are both related to the same code repo, you might have a structure like this:

    .codebuild
    ├── deploy
    │   ├── buildspec.yml
    │   ├── project.rb
    │   ├── role.rb
    │   └── schedule.rb
    └── unit
        ├── buildspec.yml
        ├── project.rb
        ├── role.rb
        └── schedule.rb

## Custom Templates

If you would like the `cb init` command to use your own custom templates, you can achieve this with the `--template` and `--template-mode` options.  Example:

    cb init --template=tongueroo/codebuild-custom-template

This will clone the repo on GitHub into the `~/.codebuild/templates/tongueroo/codebuild-custom-template` and use that as an additional template source.  The default `--template-mode=additive` mode means that if there's a file in `tongueroo/codebuild-custom-template` that exists it will use that in place of the default template files.

If you do not want to use any of the original default template files within the codebuild gem at all, you can use the `--template-mode=replace` mode. Replace mode will only use templates from the provided `--template` option.  Example:

    cb init --template=tongueroo/codebuild-custom-template --template-mode=replace

You can also specific the full GitHub url. Example:

    cb init --template=https://github.com/tongueroo/codebuild-custom-template

If you would like to use a local template that is not on GitHub, then created a top-level folder in `~/.codebuild/templates` without a subfolder. Example:

    cb init --template=my-custom # uses ~/.codebuild/templates/my-custom


## Options

```
[--force]                        # Bypass overwrite are you sure prompt for existing files
[--name=NAME]                    # CodeBuild project name
[--template=TEMPLATE]            # Custom template to use
[--template-mode=TEMPLATE_MODE]  # Template mode: replace or additive
[--type=TYPE]                    # Type option creates a subfolder under .codebuild
[--variables], [--no-variables]  # Create variables starter files
[--verbose], [--no-verbose]      
[--noop], [--no-noop]            
```
