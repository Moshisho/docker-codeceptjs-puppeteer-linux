# Dockerized Codeceptjs Puppeteer on Linux
This Dockerfile is for using CodeceptJS with Puppeteer and Mochawesome. It's configured to handle the Chromium not opening problem: https://github.com/GoogleChrome/puppeteer/blob/master/docs/troubleshooting.md without the extra steps of --no-sandbox. So run this only on applications you're certain that are secure (like the application under test in my case).
Moreover, it's leaner than what you'll find in https://github.com/Codeception/CodeceptJS/blob/master/Dockerfile since it's without the extra Nightmare package support.
To run it just use docker run codeceptjs-puppeteer-linux /bin/bash-c "node_modules/.bin/codeceptjs run --steps"

Note: It assumes you have a valid package.json and codeceptjs.conf.js files in the root you're running on. Also important to have puppeteer run with:
```"helpers": {
    "Puppeteer": {
      "chrome":{
        "args": ["--no-sandbox"]
      }
}```
