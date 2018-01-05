# Action Sheets（动作菜单）

动作菜单从设备屏幕底端向上滑动，并且显示了一组选项给与用户，用户可选择某一个动作或者取消菜单。动作菜单有时可被当做菜单的替代品来使用，但它不能用于导航。

动作菜单总是出现在页面其他组件之上，而且必须被摒弃来实现与下层内容的交互。当一个动作菜单被触发时，通过周围页面变暗使得动作菜单的选项更清晰。

*获取更多的信息，请查阅[API文档(/api/action-sheets)]*

## 使用
```TypeScript
import { ActionSheetController } from 'ionic-angular'

export class MyClass{

 constructor(public actionSheetCtrl: ActionSheetController) {}

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
       },
       {
         text: 'Archive',
         handler: () => {
           console.log('Archive clicked');
         }
       },
       {
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