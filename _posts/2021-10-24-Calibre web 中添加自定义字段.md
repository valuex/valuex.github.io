总体逻辑:通过Calibre桌面客户端进行配置。
1. 在群晖NAS上部署好Calibre-web。
2. 在群晖NAS上配置好SMB。 https://post.smzdm.com/p/a7852mld/
3. 在PC上安装好Calibre客户端。
4. 启动Calibre客户端，点击【Calibre Library】按钮
![image](https://user-images.githubusercontent.com/3627812/138579882-df8b739d-076e-4bd8-a332-b38c8c046176.png)

5. 选择第一个选项，“切换和创建书库”，在“新位置”文本框中输入Calibre Web书库在群晖中的位置

![image](https://user-images.githubusercontent.com/3627812/138579926-18cd63d5-f541-4ebb-9a35-c88756946f7f.png)

6. NAS上书库所在位置在docker "存储空间"下可见，一般配置为 \\YourNasName\\Books\Calibre

![image](https://user-images.githubusercontent.com/3627812/138580034-f7d232c0-3eb0-4290-8f9f-e4409a1abe14.png)

7. 在标题栏上右键-->选择"添加栏目"。

![image](https://user-images.githubusercontent.com/3627812/138579944-3822973f-be32-4829-ada7-dc2dd98bd9c2.png)


8.点击下面的【添加自定义栏目】按钮，输入对应字段内容即可。
![image](https://user-images.githubusercontent.com/3627812/138580113-12b61a33-1367-402e-a281-6512117e5fa4.png)


我在这里配置了一个译者，一个URL字段。刷新下Calibre web，即可看到这两个字段配置成功。
![image](https://user-images.githubusercontent.com/3627812/138580158-4bd57c71-8d0e-4ed5-be75-e34804dfb6ae.png)
