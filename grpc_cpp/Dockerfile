# Copyright The OpenTelemetry Authors
# SPDX-License-Identifier: Apache-2.0

# c++ grpc, protobuf

ARG openssl_IMAGE_TAG
ARG abseil_cpp_IMAGE_TAG
ARG base_IMAGE_TAG
ARG CMAKE_BUILD_TYPE
ARG NPROC

FROM $openssl_IMAGE_TAG as build-openssl
FROM $abseil_cpp_IMAGE_TAG as build-abseil
FROM $base_IMAGE_TAG

# need to redeclare after FROM
ARG NPROC

WORKDIR $HOME

COPY grpc grpc

COPY --from=build-abseil $HOME/install $HOME/abseil
COPY --from=build-openssl $HOME/install/openssl $HOME/openssl

WORKDIR $HOME/build/grpc

RUN cmake \
  -DCMAKE_CXX_STANDARD=17 \
  -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE} \
  -DgRPC_INSTALL=ON \
  -DgRPC_BUILD_TESTS=OFF \
  -DgRPC_BUILD_CSHARP_EXT=OFF \
  -DgRPC_BUILD_GRPC_OBJECTIVE_C_PLUGIN=OFF \
  -DgRPC_BUILD_GRPC_CSHARP_PLUGIN=OFF \
  -DgRPC_BUILD_GRPC_PYTHON_PLUGIN=OFF \
  -DgRPC_BUILD_GRPC_NODE_PLUGIN=OFF \
  -DgRPC_BUILD_GRPC_RUBY_PLUGIN=OFF \
  -DgRPC_BUILD_GRPC_PHP_PLUGIN=OFF \
  -DgRPC_ABSL_PROVIDER=package \
  -DgRPC_SSL_PROVIDER=package \
  -DOPENSSL_ROOT_DIR="$HOME/openssl" \
  -DCMAKE_PREFIX_PATH="$HOME/abseil" \
  -DCMAKE_INSTALL_PREFIX="$HOME/install" \
  $HOME/grpc

RUN nice make -j${NPROC:-3} install
