pex_binary(
    name="cowsay",
    script="cowsay",
    layout="loose",
    dependencies=[
        "3rdparty/py#cowsay",
    ],
)



docker_image(
    name="cowsay-img",
    instructions=[
        "ARG BASE_IMAGE=src/freeze:base-image",
        "FROM $BASE_IMAGE",
        "COPY src.freeze.cowsay/cowsay.pex /bin/",
        'ENTRYPOINT ["/bin/cowsay.pex"]',
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
        "ARG BASE_IMAGE=src/freeze/cowsay:cowsay-img",
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
        "ARG BASE_IMAGE=src/freeze/cowsay:cowsay-img",
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
        "ARG BASE_IMAGE=src/freeze/cowsay:cowsay-img",
        "FROM $BASE_IMAGE",
        "RUN mkdir -p /opt/etc/",
        "COPY bax.yaml /opt/etc/",
    ],
)
