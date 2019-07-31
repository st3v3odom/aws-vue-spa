# aws-cloudfront-spa

> Uses serverless framework to render a SPA to Vue-based S3 and Cloudfront


Steps I took:
1. Created a Vue app using `vue init webpack spa`
2. Moved the app related directories and files to a new app directory.
3. Copied over the 'serverless-single-page-app-plugin' from this (example Serverless repo)[https://github.com/serverless/examples/tree/master/aws-node-single-page-app-via-cloudfront].

I added that plugin to my devDependencies in package.json and ran `npm install`

That plugin expects the app it will upload to be in app/

I had to manually add `app/` to a handful of spots in the app:
  - app/build/utils.js (anywhere '../package.json' is referenced)
  - app/build/check-versions.js
  - package.json (the scripts section)

I also changed serverless-single-page-app-plugin/index #59 from app/ to app/dist so it knows to look in the build directory.

4. I created the serverless.yaml file based on the example in the )Serverless single page app example repo.)[https://github.com/serverless/examples/tree/master/aws-node-single-page-app-via-cloudfront]

I changed the name of the bucket to be one of mine.

5. I added AWS credentials via a .envrc file.



## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
