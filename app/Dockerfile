FROM node:20-alpine

ARG GH_PACKAGES_TOKEN
RUN if [ -n "$GH_PACKAGES_TOKEN" ]; then \
      npm config set //npm.pkg.github.com/:_authToken=$GH_PACKAGES_TOKEN && \
      npm config set @fabiobartoli:registry=https://npm.pkg.github.com ; \
    fi

WORKDIR /app
COPY package*.json ./
RUN npm ci --omit=dev
COPY . .
EXPOSE 3000
CMD ["npm", "start"]