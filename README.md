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

## 