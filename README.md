# Uncommon Dockerfile Bug: `ubuntu:latest` and Dependency Issues

This repository demonstrates a common but subtle bug in Dockerfiles, involving the use of `ubuntu:latest` and improper handling of dependencies.  The original Dockerfile suffers from the following:

* **Using `ubuntu:latest`:** This is discouraged for production due to potential breaking changes with updates.
* **Incorrect Dependency Order:** The `requirements.txt` is copied *before* the `RUN pip3 install`. This might lead to issues if there are base image dependencies missing.
* **Unspecified Execution Path:**  The `CMD` instruction doesn't specify the full path to the Python executable, which can be problematic depending on your setup.

The solution shows how to improve the Dockerfile for better stability and maintainability.