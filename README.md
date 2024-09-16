# GitHub Reusable Workflows

This repository contains workflows focused on verifying the functionality of
certain aspects on resuable workflows. These experiments will aid me in knowing
what I can take advantage of for automation and hopefully will answer questions
others may have on these features.

## Environments

Given that reusable workflows resolve into multiple jobs, the concept of an
"environment" doesn't make much sense as which jobs belong in that environment?
The "environment" property for a job can be sourced from an input, so the
pattern is to instead derive the environment from an input and use that where
appropriate.

## Capturing variables and secrets dynamically

Reusable workflows get access to all variables in the caller's workflow as well
as the environment they are currently situated in with their caller workflow.
They can also gain access to the secrets if `secrets: inherit` is specified.

The expressions `${{ toJSON(vars) }}` and `${{ toJSON(secrets) }}` will produce
objects of all available keys and values in the called workflow. This is
especially cool when combined with `jq` to filter this list to specific values.
For example, variables or secrets specific to a deployment can be prefixed with
`DEPLOY_` and discovered with `jq` to populate another JSON object.

Dynamic secrets can only be retrieved using `secrets: inherit`. Secrets can only
be specified if they are declared in the called workflow, meaning that you
cannot introduce them through other means. It might be better to use inputs in
this case.
