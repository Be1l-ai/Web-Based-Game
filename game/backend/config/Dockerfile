# stage 1
FROM gcc:13-bookworm AS builder

WORKDIR /app/backend

RUN apt-get update && apt-get install -y --no-install-recommends \
    cmake \
    python3 \
    pipx \
    g++ \
    build-essential \
    git \
    libsqlite3-dev \
    && rm -rf /var/lib/apt/lists/*

RUN pipx install conan

COPY conanfile.txt CMakeLists.txt ./

# change to windows profile if building on windows
COPY conan_profile_linux /root/.conan2/profiles/default
RUN /root/.local/bin/conan install . --build=missing

COPY src/ ./src/

RUN cmake -DCMAKE_BUILD_TYPE=Release . && cmake --build .

RUN mkdir -p /app/data

# stage 2
FROM debian:stable-slim

COPY --from=builder /app/backend/server_app /usr/local/bin/server_app

CMD ["/usr/local/bin/server_app"]

# Run with: (install docker muna)
    # cd game/backend
    # docker build -f config/Dockerfile .