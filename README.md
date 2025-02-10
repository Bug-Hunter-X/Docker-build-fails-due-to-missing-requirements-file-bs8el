# Docker Build Failure Due to Missing requirements.txt

This repository demonstrates a common error in Dockerfiles: the `pip install -r requirements.txt` command failing because the `requirements.txt` file is missing. This leads to a non-zero exit code during the Docker build process.

The `Dockerfile` shows the erroneous code.  The `Dockerfile_fixed` provides a corrected version which robustly handles the missing file scenario.

## Solution

The solution involves adding a check to see if `requirements.txt` exists before attempting the installation. If the file is absent, a warning message is printed, allowing the build to continue (though no python packages will be installed).

## How to reproduce
1. Clone this repository.
2. Try building the original Dockerfile (`docker build -t myapp .`). It will fail.
3. Try building the corrected Dockerfile (`docker build -t myapp_fixed .`). It will succeed, even without `requirements.txt`