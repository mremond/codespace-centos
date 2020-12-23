# [Choice] CentOS version. See: https://hub.docker.com/_/centos/
ARG VARIANT=centos7
FROM centos:${VARIANT}
ENV container docker

# This Dockerfile adds a non-root user with sudo access. Update the “remoteUser” property in
# devcontainer.json to use it. More info: https://aka.ms/vscode-remote/containers/non-root-user.
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Options for common package install script
ARG INSTALL_ZSH="true"
ARG UPGRADE_PACKAGES="true"

COPY library-scripts/common-centos.sh /tmp/library-scripts/
# Install needed packages and setup non-root user. Use a separate RUN statement to add your own dependencies.
RUN bash /tmp/library-scripts/common-centos.sh "${INSTALL_ZSH}" "${USERNAME}" "${USER_UID}" "${USER_GID}" "${UPGRADE_PACKAGES}" \
  && yum clean all \
  && rm -rf /tmp/library-scripts
