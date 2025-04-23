# Start Generation Job

This action starts a data generation job for a specified workspace and returns the job ID.

## Inputs

- `workspace_id` (required): The workspace ID (GUID) for which to start a generation job
- `api_key` (required): Structural API key for authentication
- `api_url` (optional): Structural API base URL, defaults to 'https://app.tonic.ai'
- `strict_mode` (optional): Specifies generation mode, allowed values: "NotStrict", "RejectOnSchemaActions", "RejectOnAllSchemaItems", "NotApplicable"
- `diagnostic_logging` (optional): Enables diagnostic logging, defaults to false

## Outputs

- `job_id`: The ID of the started generation job

## Example Usage

```yaml
jobs:
  start-generation:
    runs-on: ubuntu-latest
    steps:
      - name: Start Generation Job
        id: start-job
        uses: TonicAI/structural-start-job@v1
        with:
          workspace_id: ${{ secrets.STRUCTURAL_WORKSPACE_ID }}
          api_key: ${{ secrets.STRUCTURAL_API_KEY }}
          strict_mode: "RejectOnSchemaActions"

      - name: Print Job ID
        run: echo "Started job with ID ${{ steps.start-job.outputs.job_id }}"
```