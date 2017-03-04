# HXWeiboPhotoPicker

   仿微博照片选择器,支持GIF图片、多选、选原图和视频的图片选择器，同时有3Dtouch预览功能,长按拖动改变顺序.通过相机拍照录制视频  - 支持ios8.0 以上

   <img src="http://wx4.sinaimg.cn/mw690/ade10dedgy1fd9sv9phs5j20qo1bftj8.jpg" width="414" height="667">

## 一.  安装

      手动导入：将项目中的“HXWeiboPhotoPicker”文件夹拖入项目中
         只使用照片选择功能 导入头文件 "HXPhotoViewController.h"
         选完照片/视频后自动布局功能 导入头文件 "HXPhotoView.h"

## 二.  例子
### Demo1
```objc
// 懒加载 照片管理类
- (HXPhotoManager *)manager
{
    if (!_manager) {
        _manager = [[HXPhotoManager alloc] initWithType:HXPhotoManagerSelectedTypePhotoAndVideo];
    }
    return _manager;
}

// 照片选择控制器
HXPhotoViewController *vc = [[HXPhotoViewController alloc] init];
vc.delegate = self;
vc.manager = self.manager; 
[self presentViewController:[[UINavigationController alloc] initWithRootViewController:vc] animated:YES completion:nil];

// 通过 HXPhotoViewControllerDelegate 代理返回选择的图片以及视频
- (void)photoViewControllerDidNext:(NSArray *)allList Photos:(NSArray *)photos Videos:(NSArray *)videos Original:(BOOL)original

// 点击取消
- (void)photoViewControllerDidCancel

```
### Demo2
```objc
// 懒加载 照片管理类
- (HXPhotoManager *)manager
{
    if (!_manager) {
        _manager = [[HXPhotoManager alloc] initWithType:HXPhotoManagerSelectedTypePhotoAndVideo];
    }
    return _manager;
}

self.navigationController.navigationBar.translucent = NO;
self.automaticallyAdjustsScrollViewInsets = YES;

HXPhotoView *photoView = [[HXPhotoView alloc] initWithFrame:CGRectMake((414 - 375) / 2, 100, 375, 400) WithManager:self.manager];
photoView.delegate = self;
photoView.backgroundColor = [UIColor whiteColor];
[self.view addSubview:photoView];

// 通过 HXPhotoViewDelegate 代理返回 选择、移动顺序、删除之后的图片以及视频
- (void)photoViewChangeComplete:(NSArray *)allList Photos:(NSArray *)photos Videos:(NSArray *)videos Original:(BOOL)isOriginal

// 当 HXPhotoView 更新frame改变大小时
- (void)photoViewUpdateFrame:(CGRect)frame WithView:(UIView *)view

```
## 三.  更多 

   具体代码看请下载项目
   发现的哪里有不好或不对的地方麻烦请联系我,大家一起讨论一起学习进步... 
   QQ : 294005139
   <a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=294005139&site=qq&menu=yes"><img border="0" src="http://wpa.qq.com/pa?p=2:294005139:52" alt="点击这里给我发消息" title="点击这里给我发消息"/></a>
   QQ群 : 
   <a target="_blank" href="//shang.qq.com/wpa/qunwpa?idkey=ebd8d6809c83b4d6b4a18b688621cb73ded0cce092b4d1f734e071a58dd37c26">    <img border="0" src="//pub.idqqimg.com/wpa/images/group.png" alt="IOS爱好者" title="IOS爱好者"></a>
