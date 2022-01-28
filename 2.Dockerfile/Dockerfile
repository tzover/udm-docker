FROM node:14.15.4-slim
RUN apt-get update && apt-get install -y \
    curl \
    nginx
WORKDIR /home/app
# RUN touch test && echo "test" > test
RUN npx create-react-app .
CMD [ "bash" ]
