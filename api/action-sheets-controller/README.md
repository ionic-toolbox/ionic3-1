# ActionSheetController（动作菜单控制器）

一个动作菜单是让用户从一组选项里选择的对话框。它出现在应用内容的顶层，在用户与应用交互之前，它必须被用户手动摒弃。危险（有破坏性）的选项在ios系统下会很明显（如`DELETE`选项的颜色突出）。有一些简单的方法退出动作菜单，例如轻触变暗的背景或者点击桌面的返回键。

一个动作菜单由一个`buttons`数组建成，每个按钮包含`text`属性和可选的`handler`和`role`属性。如果一个`handler`返回`false`，之后动作表单将不会被摒弃。一个动作表单同样可选地拥有一个`title`，`subTitle`和一个`icon`。

一个按钮的`role`属性可被`destructive`或`cancel`。没有role属性的按钮根据不同的平台会拥有不同的缺省值。有`cancel`role的按钮总是会被作为底部的按钮加载，无论它们处于数组的哪个位置。所有其它按钮按添加到`buttons`数组的顺序来显示。注意：我们推荐`destructive`有破坏性的按钮总是数组的首位，从而使它们为顶部按钮。此外，如果动作表单因为轻触背景屏幕而摒弃，它会从有cancel role的按钮调用handler。

你可以在create方法的第一个参数里传递所有动作表单的选项：`ActionSheet.create(opts)`。另外，动作表单实例也有增加options的方法，如`setTitle()`或`addButton()`。

## 基本使用
```TypeScript
import { ActionSheetController } from 'ionic-angular';

export class MyPage {
  constructor(public actionSheetCtrl: ActionSheetController) {
  }

  presentActionSheet() {
    let actionSheet = this.actionSheetCtrl.create({
      title: 'Modify your album',
      buttons: [
        {
          text: 'Destructive',
          role: 'destructive',
          handler: () => {
            console.log('Destructive clicked');
          }
        },{
          text: 'Archive',
          handler: () => {
            console.log('Archive clicked');
          }
        },{
          text: 'Cancel',
          role: 'cancel',
          handler: () => {
            console.log('Cancel clicked');
          }
        }
      ]
    });
    actionSheet.present();
  }
}
```


## 实例成员

`config`


`create(opts)`

打开一个带有title，subTitle，和一个按钮数组的动作表单

| 参数 | 类型 | 详细 |
| ---------- | -----------|------------|
| opts | `ActionSheetOptions` | 动作表单选项 |


## 高级

动作表单create选项

| 选项 | 类型 |	描述 |
| ---------- | -----------|------------|
| title	| string | 动作表单的标题 |
| subTitle | string	| 动作表单的子标题 |
| cssClass | string	| 补充的自定义样式类，间隔空间的分离 |
| enableBackdropDismiss | boolean | 当用户轻触背景时是否摒弃动作表单 |
| buttons | array<any> | 显示按钮的数组 |

动作表单button选项

| 选项 | 类型 |	描述 |
| ---------- | -----------|------------|
| text	| string | 按钮文本内容 |
| icon | icon	| 按钮图标 |
| handler | any	| 评估按钮表示意义的函数 |
| cssClass | string | 补充的自定义样式类，间隔空间的分离 |
| role | string | 按钮应该怎样被显示，`destructive`或`cancel`。如果没有提供role，它会显示没有任何补充作用的按钮 |