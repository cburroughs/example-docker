pex_binary(
    name="datahub-cli",
    script="datahub",
    shebang="/usr/bin/env python3.10",
    layout="loose",
    # complete_platforms=("3rdparty/platforms/docker/debian/bookworm:python_310",),
    dependencies=[
        "3rdparty/py#acryl-datahub",
    ],
)

docker_image(
    name="datahub-cli-img",
    instructions=[
        "ARG BASE_IMAGE=src/freeze:base-image",
        "FROM $BASE_IMAGE",
        "COPY src.freeze.loosebigpex/datahub-cli.pex /bin/",
        'ENTRYPOINT ["/bin/datahub-cli.pex"]',
    ],
)


files(
    name="foo-yaml",
    sources=["foo.yaml"],
)


files(
    name="bar-yaml",
    sources=["bar.yaml"],
)


files(
    name="bax-yaml",
    sources=["bax.yaml"],
)


docker_image(
    name="foo-img",
    context_root="./",
    dependencies=[":foo-yaml"],
    instructions=[
        "ARG BASE_IMAGE=src/freeze/loosebigpex:datahub-cli-img",
        "FROM $BASE_IMAGE",
        "RUN mkdir -p /opt/etc/",
        "COPY foo.yaml /opt/etc/",
    ],
)

docker_image(
    name="bar-img",
    context_root="./",
    dependencies=[":bar-yaml"],
    instructions=[
        "ARG BASE_IMAGE=src/freeze/loosebigpex:datahub-cli-img",
        "FROM $BASE_IMAGE",
        "RUN mkdir -p /opt/etc/",
        "COPY bar.yaml /opt/etc/",
    ],
)

docker_image(
    name="bax-img",
    context_root="./",
    dependencies=[
        ":bax-yaml",
    ],
    instructions=[
        "ARG BASE_IMAGE=src/freeze/loosebigpex:datahub-cli-img",
        "FROM $BASE_IMAGE",
        "RUN mkdir -p /opt/etc/",
        "COPY bax.yaml /opt/etc/",
    ],
)
