# AFNetworking 3.0+ 相比之前版本的变化
新版的 AFNetworking 相比之前的版本废弃了如下三个类.

```
•	AFURLConnectionOperation
•	AFHTTPRequestOperation
•	AFHTTPRequestOperationManager
```

修改了如下几个类.

```
•	UIImageView+AFNetworking
•	UIWebView+AFNetworking.h
•	UIButton+AFNetworking.h
```

迁移方案.
用 `AFHTTPSessionManager` 代替 `AFHTTPRequestOperationManager`.
AFNetworking 2.x

```
AFHTTPRequestOperationManager *manager = [AFHTTPRequestOperationManager manager];
[manager GET:@"http://example.com/resources.json" parameters:nil success:^(AFHTTPRequestOperation *operation, id responseObject) {
    NSLog(@"JSON: %@", responseObject);
} failure:^(AFHTTPRequestOperation *operation, NSError *error) {
    NSLog(@"Error: %@", error);
}];
```

AFNetworking 3.x

```
AFHTTPSessionManager *manager = [AFHTTPSessionManager manager];
[manager GET:@"http://example.com/resources.json" parameters:nil progress:nil success:^(NSURLSessionTask *task, id responseObject) {
    NSLog(@"JSON: %@", responseObject);
} failure:^(NSURLSessionTask *operation, NSError *error) {
    NSLog(@"Error: %@", error);
}];
```

