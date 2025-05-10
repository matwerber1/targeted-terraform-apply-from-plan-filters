# targeted-terraform-apply-from-plan-filters

Generate a targeted 'terraform apply' command that only includes targets matching your change type filters. 

## Attribution

Vibe-coded with Gemini 2.5 Pro / Gemini Canvas. 

## Try it out

https://matwerber1.github.io/targeted-terraform-apply-from-plan-filters

## Usage

1. Generate a human-readable terraform plan with `terraform show -json plan | jq '.' > plan.pretty.json`

1. Load the file:
   
  <img width="896" alt="image" src="https://github.com/user-attachments/assets/7cbc174d-fab5-4218-b752-6c7f327a83a0" />

3. Create one or more filter groups to select a subset of changes from the plan:

  <img width="359" alt="image" src="https://github.com/user-attachments/assets/2302bec6-aea0-4284-9cd8-59bb2b5f9ea7" />

4. Results of the filter groups are consolidated and deduped in the table at the bottom. Optionally, further refine the selection and click **Copy as CSV** when satisfied:

  <img width="1320" alt="image" src="https://github.com/user-attachments/assets/6f4d5cfe-b22a-4ca0-a6e1-737fc0781cd2" />

5. Concatenate the "target result flag" values as arguments to a `terraform apply` command and run for a targeted apply. Append to `terraform plan` to confirm the command is well-formed.


## TODO

1. Fix the output table to add missing dash (`-`) prefix to each `target=` keyword, e.g. `-target=XYZ` instead of `target=XYZ`
2. Add ability to generate consolidated command based on final target selections and copy to clipboard instead of expecting user to copy CSV output and form the final command themselves.
3. Add ability to switch between generating a targeted `terraform plan` vs. a targeted `terraform apply`
