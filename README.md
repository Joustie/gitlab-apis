# gitlab-apis

The most comprehensive gitlab api, almost covers all gitlab apis. Also, we provide a isomorphic api which can be used both in browser and Node.js.
---

## Install

```bash
tnpm i @ali/gitlab-apis -S
```

## Usage

> Each API returns a Promise instance, and resolves with result.  
> Find more samples in tests.

### Issues APIs

- Firstly create your API set

```js
const issues = require('@ali/gitlab-apis').issues;
const project_id = 85921;

const apis = issues(project_id, {
  private_token: 'N22MqwZ1hytQFXQXcD2g',
});
```

- Then you can call the APIs below

  - apis.create(data) `Create issue`  
  `@param` data.title {string} (required) - The title of an issue  
  `@param` data.description {string} (optional) - The description of an issue  
  `@param` data.assignee_id {number} (optional) - The ID of a user to assign issue  
  `@param` data.labels {string} (optional) - Comma-separated label names for an issue  
  `@returns` {object} The newly created issue  

  ```js
  apis.create({
    title: 'test task',
    description: 'description of test task',
    assignee_id: 7214,
    labels: 'test',
  }).then((r) => {
    console.log(r);
  });
  ```

  - apis.list(data) `List issues`  
  `@param` data.page {number} (optional) - Current page number  
  `@param` data.per_page {number} (optional) - Page size  
  `@param` data.iid {number} (optional) - Return the issue having the given iid  
  `@param` data.state {string} (optional) - Return all issues or just those that are opened or closed  
  `@param` data.labels {string} (optional) - Comma-separated list of label names  
  `@param` data.order_by {string} (optional) - Return requests ordered by created_at or updated_at fields. Default is created_at  
  `@param` data.sort {string} (optional) - Return requests sorted in asc or desc order. Default is desc  
  `@returns` {array} The list of matched issues  

  ```js
  apis.list({
    state: 'opend',
    labels: 'test',
  }).then((r) => {
    console.log(r);
  });
  ```

  - apis.view(issue_id) `View issue`  
  `@param` issue_id {number} (required) - The ID of a project issue  
  `@returns` {object} The matched issue  

  ```js
  apis.view(123456).then((r) => {
    console.log(r);
  });
  ```

  - apis.update(issue_id, data) `Update issue`  
  `@param` issue_id {number} (required) - The ID of a project issue  
  `@param` data.title {string} (optional) - The title of an issue  
  `@param` data.description {string} (optional) - The description of an issue  
  `@param` data.assignee_id {string} (optional) - The ID of a user to assign issue  
  `@param` data.labels {string} (optional) - Comma-separated label names for an issue  
  `@param` data.state_event {string} (optional) - The state event of an issue ('close' to close issue and 'reopen' to reopen it)  
  `@returns` {object} The updated issue  

  ```js
  apis.update(123456, {
    state_event: 'close',
  }).then((r) => {
    console.log(r);
  });
  ```

### Users APIs

- Firstly create your API set

```js
const users = require('@ali/gitlab-apis').users;

const apis = users({
  private_token: 'N22MqwZ1hytQFXQXcD2g',
});
```

- Then you can call the APIs below

  - apis.search(keywords) `Search users`  
  `@param` keywords {string} (required) - Search keywords  
  `@returns` {array} Search results  

### Basic Network APIs

You can use network APIs to create any API wrapper by yourself.

> View `lib/network.js` for samples.

## LInks

- [Gitlab APIs](http://gitlab.alibaba-inc.com/help/api/README.md)
