# API Security Validator

This project provides an automated security maturity gate for API specifications using GitHub Actions. It validates the security posture of your API by parsing a YAML file and calculating a security maturity score.

## Project Structure

```
contracts/
  df/
    tr-test-petstore-java/
      openapi.yaml
      .api-security.yaml
.github/
  workflows/
    security-gate.yaml
```

## How It Works
- The GitHub Actions workflow (`.github/workflows/security-gate.yaml`) runs on pull requests to `main` and `master` branches.
- It uses `yq` to parse the API security maturity score from the YAML file at `contracts/df/tr-test-petstore-java/openapi.yaml`.
- The workflow checks if the score meets a minimum threshold before allowing merges.

## Usage
1. Update your API security maturity data in `.api-security.yaml` under `contracts/df/tr-test-petstore-java/`.
2. On pull requests, the workflow will automatically validate the score.
3. If the score is below the threshold, the workflow will fail and provide instructions to improve your API security.

## Requirements
- GitHub Actions
- `yq` (installed automatically in the workflow)

## Customization
- Adjust the minimum score threshold in the workflow file as needed.
- Modify the YAML parsing logic to fit your API security maturity model.

## License
MIT
