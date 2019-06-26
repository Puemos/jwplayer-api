# jwplayer-api [![Build Status](https://travis-ci.org/puemos/jwplayer-api.svg?branch=master)](https://travis-ci.org/puemos/jwplayer-api) [![Greenkeeper badge](https://badges.greenkeeper.io/puemos/jwplayer-api.svg)](https://greenkeeper.io/)

> A wrapper for jwplayer platform API


## Install

```
$ npm install --save-dev jwplayer-api
```


## Usage

```js
'use strict';

const axios = require("axios");
const JwplayerApi = require('jwplayer-api');

const api = new JwplayerApi({
    key: "myKey",
    secret: "mySecret"
});

const myApi = {
    getUploadUrl: params => {
        return api.getUploadUrl(params);
    },

    delete: video_key => {
        return api.delete(video_key);
    },

    getVideoDetails: video_key => {
        return axios({
            method: "get",
            url: api.generateUrl("v1/videos/show", {
                video_key
            })
        }).then(res => {
            return res.data;
        });
    },

    conversionCreate: (video_key, template_key) => {
        return api.conversionCreate(video_key, template_key);
    }
};
```

## License

MIT © Shy Alter
