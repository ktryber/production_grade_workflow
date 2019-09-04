# you can use as <name> to tag the phase
FROM node:alpine as build_phase

WORKDIR '/app'

COPY package.json .

RUN npm install

COPY . .

RUN npm run build

# Previous build phase is complete, now start executing
# the run phase
FROM nginx as run_phase

COPY --from=build_phase /app/build /usr/share/nginx/html
