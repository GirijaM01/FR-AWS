ARG IDM_REPO=gcr.io/forgerock-io/idm/pit1
# replace this tag when idm is promoted
#ARG IDM_TAG=7.0.0
ARG IDM_TAG=7.0.0-60716b9fec0307a99f820822e43b886824088b2b
FROM $IDM_REPO:$IDM_TAG

# Harden IDM by removing the Felix OSGI Console. Unless you are a ForgeRock developer, the
# console is rarely required. Your configuration should NOT include conf/felix.webconsole.json
RUN rm bundle/org.apache.felix.webconsole*.jar  && \
    rm bundle/openidm-felix-webconsole-*.jar

# Removes any existing conf files that might conflict with our config. This includes the embedded ds repo.
RUN rm -fr /opt/openidm/conf
ENV JAVA_OPTS "-server -XX:MaxRAMPercentage=75"
COPY --chown=forgerock:root . /opt/openidm
