FROM node:20-slim

WORKDIR /app/frontend

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    git \
    g++ \
    cmake \
    ninja-build \
    && rm -rf /var/lib/apt/lists/*

COPY package*.json ./

RUN npm install --silent

COPY src/ ./src/

CMD ["npm", "run", "build"]

# Run with: (install docker muna)
    # cd game/frontend
    # docker build -f config/Dockerfile .