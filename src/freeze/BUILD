docker_image(
    name="base-image",
    instructions=[
        "FROM public.ecr.aws/docker/library/python:3.10-bookworm",
        """
        RUN \
        export DEBIAN_FRONTEND=noninteractive && \
        apt-get update -y && \
        apt-get install -y --no-install-recommends cowsay && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists/*
        """

    ],
)
