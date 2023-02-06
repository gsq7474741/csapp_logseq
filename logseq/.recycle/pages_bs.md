- B 站专栏为啥不支持 Markdown…懒得改了 封面 pid 80969788
  
  去我博客获取更优阅读体验 https://intoyour.space/create-your-own-beat-saber-avatar-from-scratch/
## 注意



这篇文章不会讨论人物模型怎么获得，请确保您手上已有可用的人形 (humanoid) 模型可用再继续向下阅读。
## 前期准备 [（跳至下节）](#modelProcessing)
### 模组安装



显然原版 Beat Saber 并不支持导入自定义人物模型，所以我们需要安装 [Custom Avatar](https://github.com/nicoco007/BeatSaberCustomAvatars) 模组。



最简单的方式就是打开 Mod Assistant，勾选 `Custom Avatar`，然后按 `Install or Update`



![安装 Custom Avatar 模组](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-111042.png)
### 下载模板项目文件



打开 Custom Avatar 模组的 [Github Release 页面](https://github.com/nicoco007/BeatSaberCustomAvatars/releases/) 下载 `BeatSaberCustomAvatars-版本号-UnityProject.zip`



![下载模板项目文件](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-000958-300x112.png)



将 zip 文件解压到任意位置。打开 Unity Hub 并导入项目文件夹。
### 下载对应版本的 Unity Editor [（如编辑器未缺失可点击跳至下节）](#copyLibraryFiles)



打开项目，此时 Unity Hub 会提示项目使用了未安装的编辑器版本。此处是 `2019.3.15f1`，我们需要使用尽可能相近的版本打开项目。



![未安装的编辑器版本](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-001405-300x127.png)



前往 [Unity Archive](https://unity3d.com/get-unity/download/archive)，找到对应的版本，点击 `Unity Hub` 按钮。



![Unity Archive 页面](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-001445-1-300x169.png)



回到 Unity Hub，直接点击安装，开始下载 Unity Editor。



![下载 Unity Editor](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-001555.png)



<h3 id="copyLibraryFiles">复制库文件</h3>



打开游戏目录文件夹（打开 Steam，右键游戏 > 管理 > 浏览本地文件；Oculus 版请自行 Google），打开 `Beat Saber_Data/Managed/` 文件夹，复制 `DynamicBone.dll` 和 `FinalIK.dll` 两个文件



![复制库文件](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-002931.png)



到之前下载的 Custom Avatar 模板项目文件夹 `Assets/Library/` 文件夹。



![复制到目标文件夹](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-003003.png)



回到 Unity Hub 打开项目，取决于你拥有的模型的不同
- 将 `.fbx` 拖入 Unity Editor 窗口
- 双击 `.unitypackage` 设置导入选项
  
  - 如果你的模型有 Dynamic Bone 对应，最好也预先导入 Dynamic Bone 脚本
- 使用 [UniVRM](https://github.com/vrm-c/UniVRM) 导入 `.vrm` 模型
- 等等
  
  
  
  具体如何导入请咨询模型作者、查询脚本文档等。
  
  
  
  ![导入模型](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-003157.png)
  
  
  
  <h2 id="modelProcessing">模型处理</h2>
### 修补 VRChat 模型与添加 Dynamic Bone[（其他模型所有者及不需 Dynamic Bone 者可按这里跳过）](#fixShader)



点击导入的 VRChat 人物的 prefab，在 Inspector 将两个丢失的脚本删除。这两个脚本是 VRChat 用来识别人物数据的，在 Beat Saber 中无用。



![删除 missing scripts](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-003313.png)



展开左侧 Hierarchy 中的人物，找到拥有 Dynamic Bone 的骨骼。右键 Copy Component 复制组件。



![copy component](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-015428.png)



点击 Add Component 添加组件，搜索 Dynamic Bone，添加 Beat Saber 版的 Dynamic Bone 组件。（可以用名字前的 `#` 或是 `C#` 区分，至少在我这里是这样）



![add component](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-015435.png)



添加完成后右键 `C#` Dynamic Bone，点击 Paste Component Value，粘贴参数或自行调整参数。右键 `#` Dynamic Bone，点击 Remove Component 删除组件。如果骨骼同时拥有 Dynamic Bone Collider，以同样步骤添加 `C#` Dynamic Bone Collider 进行替换。



![paste component values](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-015448.png)



将此步骤重复直至全部拥有 Dynamic Bone 或 Dynamic Bone Collider 的骨骼全部替换完毕。



<h3 id="fixShader">修复 Shader</h3>



Beat Saber 只支持自家 shader，如果使用 UTS 这些会导致模型在游戏中变成纯白色（虽然但是如果你萌全白那也不是不行）。



![show UTS](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-003418.png)



点击切换 shader 搜索 `Unlit Glow`（理论上任何在 `BeatSaber/` 里的 shader 都能用，但是我没测试过）。



![search for Unlit Glow](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-003434.png)



跟其他 shader 一样，给 Unlit Glow 加上贴图



![add texture](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-003458.png)



注意：如果材质有**透明**部分的话需要使用 `Unlit Glow Cutout Dithered`，不然像**胖次**的花边这样的地方就会有黑色背景。



![pantsu](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-130204.png)
## 添加骨骼绑定
### 添加空物体与调整模型大小



将模型拖入 Hierarchy，在 Hierarchy 里右键点击 Create Empty 创建八个空物体，分别命名为 `角色名`、**`Body`**、**`Head`**、**`LeftHand`**、**`RightHand`**、**`Pelvis`**、**`LeftLeg`**、**`RightLeg`**（后三个仅全身追踪需要）



![添加空物体](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-003658.png)



创建一个 Cube 正方体，将 Y 轴的 scale 缩放设置为人体高度（约为1.7），X、Y 轴保持为 1；将 Y 轴 position 位置设置为 scale 的一半（这里是 0.85），X、Z 轴保持为 0。



![Cube dimensions](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-004112.png)



将模型的 X、Y、Z 轴 position 位置均调整至 0，



![model dimensions](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-004104.png)



调整模型 scale 缩放直至与长方体差不多大



![resize model](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-004121.png)



此时可以删除或隐藏长方体。
### 调整空物体



 将 `角色名` 和 `Body` 两个空物体的 position 位置全部设置为 0。并把 `Head`（头）、`LeftHand`（左手）、`RightHand`（右手）、`Pelvis`（骨盆）、`LeftLeg`（左腿）、`RightLeg`（右腿）分别放到模型的对应位置。



`Head` 物体需要放置在眼部，就是你想要进入游戏第一人称时摄像机放在哪。



![head](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-004207.png)



`Pelvis` 和 `LeftLeg`、`RightLeg` 这三个空物体需要放在全身追踪 tracker 对应的身体部位（不过我没有全身追踪的 tracker 所以我也没法测试具体有什么影响；之前测试过[用 Oculus Rift 来全身追踪](https://youtu.be/gwuQrF8-R-4)，但是在我这里极其不稳定导致没有什么实用价值）。



![pelvis](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-004328.png)



![leg](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-004406.png)



将模型和其他七个空物体拖入 `角色名` 空物体中，成为它的子物体。



![拖入空物体](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-013027.png)
### 创建 Target



找到上述六个身体部位在模型里的骨骼，右键骨骼点击 Create Empty 创建空物体。这一步是为了创建一个与骨骼位置完全相同的空物体。



![创建空物体](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-013311.png)



将这个空物体命名为 `对应部位Target`，即 **`HeadTarget`**、**`LeftHandTarget`**、**`RightHandTarget`**、**`PelvisTarget`**、**`LeftLegTarget`** 或 **`RightLegTarget`**。并拖到之前创建的 `对应部位` 空物体中。



![拖入对应部位空物体](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-013332.png)
### 设置 VR 追踪



点击模型物体，在 Inspector 里点击 Add Component 添加 `VRIK Manager` 组件。



![设置 VRIK Manager](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-013616.png)



对于需要全身追踪的模型，取消勾选 Plant Feet。



![取消勾选 plant feet](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-013633.png)



在下面 `Spine` 的 `Head Target` 和 `Pelvis Target` 和 `Left Hand`、`Right Hand`、`Left Leg` 、 `Right Leg` 里的 Target 分别设置为之前创建的 `对应部位Target` 物体。



![设置Target](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-131351.png)



![设置Target1](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-130342.png)



![设置Target2](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-130349.png)



![设置Target3](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-130356.png)



![设置Target4](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-130404.png)
## 准备导出
### 设置角色



点击 `角色名` 空物体，点击 Add Component 添加两个组件：Avatar Descriptor 和 First Person Exclusion。
#### Avatar Descriptor



Name（名字）、Author（作者）按照自己喜欢来填写



![设置角色](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-131717.png)



填好之后找一张喜欢的正方形图片，直接拖入 assets 窗口



![设置封面](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-132334.png)



点击图片，在 Inspector 里将 Texture Type 改为 Sprite (2D and UI)，点击 Apply 应用。回到 `角色名` 空物体，在 Avatar Descriptor > Cover 选择刚刚导入的图片作为封面。
#### First Person Exclusion



所有在这里的物体在第一人称下都不会显示，推荐将这几个身体部位隐藏：头、头发、耳朵（兽耳）、眼镜、发饰等头部物体（不过可能调整一下摄像机还真的能第一人称假装戴眼镜，那还挺酷的，有兴趣的可以自己试一下）。



将 Size 后的数字调整为需要隐藏的物体数量，在下面的 Element 里选择需要屏蔽的物体即可
### 导出角色



最后点击顶部菜单栏 `Window > Avatar Exporter`，在弹出的窗口里确认信息无误后点击 Export 角色名即可。



![打开导出窗口](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-013758.png)



将导出的 `角色名.avatar` 复制到 Beat Saber 游戏目录的 `Custom Avatars\` 文件夹里



![导出文件](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-21-013835.png)
## 游戏内
### 启用自定义角色



![](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-135528.png)



![](https://intoyour.space/wp-content/uploads/2022/06/Screenshot-2022-06-22-135624.png)
### 游戏内效果



（等我啥时候玩的来了录个视频） 作者：一坨土豆泥- https://www.bilibili.com/read/cv17220085 出处：bilibili