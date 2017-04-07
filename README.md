## 目录
- [网络请求](#1)
  - [POST方法](#1.1)
  - [GET方法](#1.2)
- [页面加载](#2) 

<h2 id="1"><font color=#6495ED> 网络请求 </font></h2>
- <h4 id="1.1">POST方法 </h4>

需要借助AFNetworking

    NSString *url = @"http://xxxxxxxxxxxxxxxxxxxx";
    NSDictionary *param = @{@"key":@"value"};
    AFHTTPSessionManager *manager = [[AFHTTPSessionManager alloc] initWithSessionConfiguration:[NSURLSessionConfiguration defaultSessionConfiguration]];
    manager.requestSerializer = [AFJSONRequestSerializer serializer];
    [manager.requestSerializer setValue:@"application/x-www-form-urlencoded" forHTTPHeaderField:@"Content-Type"];
    [manager POST:url parameters:param progress:nil success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
        NSLog(@"成功%@", responseObject);
    } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
        NSLog(@"失败%@", error);
    }];

- <h4 id="1.2">GET方法 </h4>

需要借助AFNetworking

    NSString *url = @"http://xxxxxxxxxxxxxxxxxxxx; //网址
    NSDictionary *param = @{@"key":@"value"};//参数
    AFHTTPSessionManager *manager = [AFHTTPSessionManager manager];
    manager.responseSerializer = [AFHTTPResponseSerializer serializer];
    [manager GET:url parameters:param progress:nil success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
        id json = [NSJSONSerialization JSONObjectWithData:responseObject options:0 error:nil];
        NSLog(@"KEY :%@",[json valueForKey:@"KEY"]);
    } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
        NSLog(@"错误:%@",error);
    }];
    


<h2 id="2"><font color=#6495ED> 页面加载 </font></h2>
- <h4 id="2.1"> Xib页面加载方式 </h4>
	1. 首先：新建 ****.xib* 文件，并将其*File's Owner* 中的 Custom Class设置成对应的 ****ViewController*
	2. 然后：在对应的 ****ViewController* 中添加如下代码

```
[[NSBundle mainBundle]loadNibNamed:@"XXXX" owner:self options:nil];
// XXXX为XXXX.xib文件的文件名，不要带.xib
```