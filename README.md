# NotesApp
北京邮电大学网络空间安全学院

2020级网安**软件工程技术基础**课程大作业

Coursework based on MiNotes
[TOC]
# 学习记录 for MiNote
---
## 2022.4.14

### Done

- 解决了**问题①**：[解决方法](https://www.cnblogs.com/liaojie970/p/5718901.html)。
    `NotesListActivity`继承自`Activity`，要使用`android:showAsAction`而不是`app:showAsAction`。

---
## 2022.4.13

### Done
- 重写了`.ui.NotesListActivity`的`676: onBackPressed() `方法，实现了双击退出程序。
    ```Java
    @Override
    public void onBackPressed() {
        long secondTime = System.currentTimeMillis();
        if (secondTime - firstTime   2000) {
          Toast.makeText(MainActivity.this, "再按一次退出程序", Toast.LENGTH_SHORT).show();
        firstTime = secondTime;
        } else {
        System.exit(0);
    }
    ```

- 重写了`.ui.NotesListActivity`的`onPrepareOptionsMenu(Menu menu)`方法，该方法是为了在不同界面显示不同的Menu选项，在此添加了recycle_bin的Menu选项
    ```Java
    else if(mState == ListEditState.RECYCLE_BIN){
            //此处需要设计回收站的menu,定义为recycle_menu
            //getMenuInflater().inflate(R.menu.recycle_bin, menu);
        } else{
    ```
- 修改了`menu/note_list`菜单布局，初步设想是：
    - 取消底部的写标签按钮，将新建标签的按钮引入到ActionBar来适应新版本Android。

    ==问题①：== 当修改了`menu/note_list`后，布局预览正常，但是当软件安装运行后修改后的布局却没有在ActionBar中显示出来。

### ToDo List
- 解决问题①
- 推进`.ui.NotesListActivity`的阅读
- 了解**有没有版本管理的方法**，每次修改回滚真的好累（

---

## 2022.4.12

### Done
- 使用插件对项目model文件夹构造类**UML图**
- 学习了Uri、Context的机制和基础方法，如`Uri.parse()`。
- 阅读了model文件夹下的Note和WorkingNote
    ==*疑惑：*== data中的Notes类中接口如何在`model.Note`和`model.WorkingNote`中直接使用
- **重点阅读**了`model.WorkingNote`类（第114行）
- 略读了`.ui.NotesListActivity`活动
    - 在`.ui.NotesListActivity`中有关**删除**的方法：
        - `480: private void batchDelete() //批量删除`
        - `517: private void deleteFolder(long folderId) //删除文件夹` 
    - `676: onBackPressed() `方法根据当前所处界面来选择Back键对应操作，可能需要添加**回收站界面**对应的返回操作


### Todo List
- 继续阅读`model.WorkingNote`类（第114行）
- 继续阅读`.ui.NotesListActivity`，从`initResources()`方法开始

