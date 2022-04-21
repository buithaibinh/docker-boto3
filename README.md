Using the Boto3 Docker image
===================================

A Docker image for running Boto3 scripts.

Build the Docker image locally
------------------------------

    docker buildx build --platform linux/amd64 -f ./Dockerfile -t binhbv/boto3 .
    docker tag binhbv/boto3:1.8 binhbv/boto3:1.8
    docker push binhbv/boto3:1.8

Run
---

    docker run -it binhbv/boto3:1.8 python
    docker run -v $PWD/test:/tmp binhbv/boto3:1.8 python test.py

To run a task that talks to AWS you have to export your AWS credentials to the environment:

    export AWS_DEFAULT_REGION=us-west-2
    export AWS_ACCESS_KEY_ID=...
    export AWS_SECRET_ACCESS_KEY=...

    docker run -v $PWD/test:/tmp \
    -e AWS_ACCESS_KEY_ID -e AWS_SECRET_ACCESS_KEY -e AWS_DEFAULT_REGION \
    binhbv/boto3:1.8 python test.py

