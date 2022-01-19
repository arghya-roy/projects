curl -sL https://rpm.nodesource.com/setup_14.x | bash -

sudo yum install -y nodejs

node -v
npm -v

git clone https://github.com/sumant-mishra/node-app.git
cd node-app

npm install
node index.js

if we want to run it using npm start then we have to add a 
script in package.json
"scripts": {
    "start": "node your-script.js"
}
npm start

FROM node
COPY node-app/ .
RUN npm install
EXPOSE 3100
CMD npm start
