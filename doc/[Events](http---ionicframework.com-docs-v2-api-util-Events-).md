
# [Events](http://ionicframework.com/docs/v2/api/util/Events/)
Events是一个发布订阅式的事件系统。

```
// first page (publish an event when a user is created)
function createUser(user) {
  console.log('User created!')
  events.publish('user:created', user);
}

// second page (listen for the user created event)
events.subscribe('user:created', (user) => {
  console.log('Welcome', user);
});

```

## 实例方法

### `subscribe(topic,handler)`

订阅某个事件，当有该事件被发布时，执行handler。

- topic `string`

	订阅的主题

- handler `function`

### `unsubscribe(topic, handler)`
取消订阅某个主题。handler不再接受该主题发布的事件。

如果handler成功移除，改函数返回`true`

### `publish(topic,eventData)

将事件发布到给定的主题

