---
layout: post
title:  "关于把Pokemon从模拟器Gen3洗白的记录"
date:   2025-05-07 13:50:47 +0200
tags: [Pokémon, Emulation]
permalink: /pokemon-migration/
---

# Background
倒腾旧电脑从硬盘里翻出了08年的绿宝石386存档，在亲自魔的闪光梦幻/999HP会飞天术寄生种子巨沼怪中翻出了少量正经存档，看着手里的NS起了歹念，折腾开始。

（虽然时不时怀疑自己借用别人存档+打开PKHex检查合法性的行为和直接魔到底有什么区别，但执念和洁癖本来就挺唯心的，那我觉得它们是以前的六只它们就是吧www）

# 传输
当前进度：
- 模拟器：绿宝石386（基于日版） -> 日文原版绿宝石 -> 魂银（日版）-> 黑（美版）
- 3DS -> NS：Y -> Bank -> HOME

## Gen3 -> Gen4
- 关于64KB和128KB的sav档，64KB到128KB的魔改方法暂时没找到([this doesn't work](https://projectpokemon.org/home/forums/topic/38362-converting-64kb-to-128kb-3rd-gen/))，但是[structure](https://bulbapedia.bulbagarden.net/wiki/Save_data_structure_(Generation_III))；64kb是导出的battery file，128kb应该是在gba文件隔壁/BATTERY folder下面能找到的）
- mGBA的128kb sav在gba文件文件夹下，vba under BATTERY folder
- DeSmuME 
    - [Youtube](https://www.youtube.com/watch?v=QHKlnYfglFk)
    - [Trying Pal Park transfer from Pokemon Emerald to Pokemon Diamond on DeSmuME](https://gbatemp.net/threads/trying-pal-park-transfer-from-pokemon-emerald-to-pokemon-diamond-on-desmume.560355/)
- MelonDs （试过，和DeSmuME差不多，没啥软用）
- Mumu模拟器+DraStic（cite bilibili [宝可梦从GBA到nds nds到3dS 3ds模拟器到正版机器粗略演示](https://www.bilibili.com/video/BV1NV4y1p7em/?vd_source=89b3974c5e7d7c89a9b8550de9bf509c)，唯一一个识别到了gen3卡槽的）
- mention that 日版gen4只能读对应语言版本的gen3
- 如果能找到但是说存档损坏（日英双语方便搜索），在gen3游戏内save一下就好
    - Like this: ![image](../assets/fig/2025-05-07-pkm-migration/damaged_U.png) ![image](../assets/fig/2025-05-07-pkm-migration/damaged_JP.jpg)

### 存档要求
- gen3 全国图鉴
    - [Pocket Monsters : Emerald [Japan]](https://wowroms.com/en/roms/nintendo-gameboy-advance/download-pocket-monsters-emerald-japan/13807.html)
    - [Pokemon - Emerald Version](https://www.emulatorgames.net/roms/gameboy-advance/pokemon-emerald-version/)
    - [Pokémon Ruby Version [save file] 2023-04-16](https://gbatemp.net/download/pokemon-ruby-version-save-file.37934/)
    - [Pokémon Emerald Version [save file] 2023-08-25](https://gbatemp.net/download/pokemon-emerald-version-save-file.38072/)
- gen4 在pal park
    - [SoulSilver ROM(JP)](https://www.emulatorgames.net/roms/nintendo-ds/pokemon-soul-silver-jp/)
    - [SoulSilver ROM(U)](https://www.emulatorgames.net/roms/nintendo-ds/pokemon-soulsilver-version/)
    - [Pokemon SoulSilver Version - Complete Save (100%) 1.1](https://gbatemp.net/download/pokemon-soulsilver-version-complete-save-100.38214/)

### 绿宝石386 -> 原版绿宝石
原版没法读取魔改版存档，用修改器直接写内存（修改器原作者: Fuzzier(Gauchyler@etang.com) ）

VBA v1和v2，v1能开魔改版，v2能开原版；修改器只能改v1的动态内存（因为存档compatibility的问题，都打算直接copy内存了，突然发现原版可以读取魔改版的存档内容，不用魔了）

## Gen4 -> Gen5

用到的功能应该是Download Play，目前支持这个的模拟器应该只有MelonDS。

### 存档要求
- gen4 大概不太有什么要求，但毕竟前一步都要求再pal park了，就默认在了吧
- gen5 需要人在传输工厂，和npc对话之后host这个传输过程

- **TODO**：把能用的ROM pairs放上来

### TroubleShooting
总是连接错误或者显示没有compatible的游戏卡带（根据各论坛的说法的诱因可能有：
- gen4和gen5的卡带语言版本不同（日版/美版/欧陆各语言版）
    ![image](../assets/fig/2025-05-07-pkm-migration/gen4-5NoCompatible.png)
    *不兼容就是不兼容（被气到想直接PKHex复制内存的程度）*
- 存档和卡带的语言版本不同可能会有影响？（总之为了减少无关变量我全改成了英文版存档，但理论上没问题）
    ![image](../assets/fig/2025-05-07-pkm-migration/gen4-5Dont.png)
    *不建议这么干（以及直接用DSi的Console比较好）*
- 为了防止引入奇怪变量，建议时不时用PKHex检查存档及pokemon的合法性（毕竟从奇妙改版掏出来的东西或多或少有机会不对劲） ![image](../assets/fig/2025-05-07-pkm-migration/illegal_pkHex.png)

### 步骤记录
- 虽然其他教程说直接用DS的BIOS7和BIOS9 firmware就可以work，但可能年代久远（？），最后我是用了melonDS的DSi模拟器，并且gen4作为wifi的host机，gen5加入连接才成功的（不太清楚为什么反过来容易连接错误（比如这样：
    ![image](../assets/fig/2025-05-07-pkm-migration/gen4-5melonDS_comErr.png)
- 多个教程均提到帧率越高越容易成功链接（不知道原理）。实操的时候建议melonDS双开的时候可以一个关掉帧率限制，另一个用快捷键控制是否锁帧（回自动同步），如果直接两个都开无限制的话会卡死闪退。
- 成功了大概是这样，选就完事了
    ![image](../assets/fig/2025-05-07-pkm-migration/gen4-5Succ.png)

### 碎碎念
- 捕捉的套圈小游戏还挺好玩的，接下来不知道直接送去实体机还是先送到gen6再去实体机（反正gen6就可以进bank，懒得再折腾去日月了（绝对不是因为充了一个月home会员不想续费，也不是因为做毕设和期末考试太忙，嗯嗯））

## Gen6 -> Bank -> Home
有3ds实体机所以毫无技术含量，对Gen6的存档没有任何要求，只要box里有pkm就行（以及3ds能联网）
### Gen6 -> Bank
进Bank，好像需要注册一个3ds账号，全免费直接照着做就行，然后就是呆呆兽也可以学会的简单操作
### Bank -> Home
难度极高，主要体现为需要给Home氪金

# Reference
- 感觉是市面上最全的一个: [Guide: How to transfer a Pokemon through different generations using emulation](https://www.reddit.com/user/Porta_14/comments/lxbjwv/guide_how_to_transfer_a_pokemon_through_different/#:~:text=In%20your%20generation%204%20games,your%20save%20file%20as%20a%20%5B.)

- [贴吧沙奈朵真爱哥（【攻略】来自漆黑的全缎带沙奈朵travel in time and space）](https://tieba.baidu.com/p/6508898552?pn=1)）