# Run correlation

For every failure, record:

- workflow name
- workflow run ID and URL
- job ID and job name
- head branch/ref
- head commit SHA
- failing step
- relevant log excerpt

Before editing, confirm that the commit SHA in the run matches the source state being inspected. When a user supplies an older log, do not attribute it to the current commit without verification.
