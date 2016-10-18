# gitlab-apis

---

The most comprehensive gitlab api, almost covers all gitlab apis. Also, we provide a isomorphic api which can be used both in browser and Node.js.

## Install

```bash
tnpm install --save gitlab-apis
```

## Usage

```
const GitlabApis = require('gitlab-apis');

const client = GitlabApis({
  // the gitlab url
  base_url: 'http://gitlab.alibaba-inc.com',
  private_token: '',
  timeout: 3000,
});

// return a promise object
const ret = apis.projects.list({search: 'xx'});
```
