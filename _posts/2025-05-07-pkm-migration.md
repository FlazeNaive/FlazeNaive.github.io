---
layout: post
title:  "把Pokemon从模拟器Gen3洗白的小日记"
date:   2025-05-07 13:50:47 +0200
categories: [Pokemon, Emulation]
permalink: /pokemon-migration/
---

# 从模拟器Gen3洗白Pokemon的小笔记
## Background
倒腾旧电脑从硬盘里翻出了08年的绿宝石386存档，在亲自魔的闪光梦幻/999HP会飞天术寄生种子巨沼怪中翻出了少量正经存档，看着手里的NS起了歹念，折腾开始。

## 传输
当前进度：绿宝石386（基于日版的翻译） -> 日文原版绿宝石 -> 魂银（日版）
### Gen3 -> Gen4
- VBA v1和v2，v1能开魔改版，v2能开原版；修改器只能改v1的动态内存（提一下64KB和128KB的sav档，64KB到128KB的魔改方法暂时没找到，但是[structure](https://bulbapedia.bulbagarden.net/wiki/Save_data_structure_(Generation_III))；64kb是导出的battery file，128kb应该是在gba文件隔壁/BATTERY folder下面能找到的）
- mGBA的128kb sav在gba文件文件夹下，vba needs to be checked, likely under BATTERY folder
- DeSmuME （[Youtube](https://www.youtube.com/watch?v=QHKlnYfglFk)，Reddit(in reference), [贴吧](https://tieba.baidu.com/p/6508898552?pn=1)）
- MelonDs （试过，和DeSmuME差不多，没啥软用）
- Mumu模拟器+DraStic（cite bilibili [宝可梦从GBA到nds nds到3dS 3ds模拟器到正版机器粗略演示](https://www.bilibili.com/video/BV1NV4y1p7em/?vd_source=89b3974c5e7d7c89a9b8550de9bf509c)，唯一一个识别到了gen3卡槽的）
   - （add file structure）
- mention that 日版gen4只能读对应语言版本的gen3
- 如果能找到但是说存档损坏（日英双语方便搜索），在gen3游戏内save一下就好
#### 存档要求
- gen3 全国图鉴
    - [Pocket Monsters : Emerald [Japan]](https://wowroms.com/en/roms/nintendo-gameboy-advance/download-pocket-monsters-emerald-japan/13807.html)
    - [Pokemon - Emerald Version](https://www.emulatorgames.net/roms/gameboy-advance/pokemon-emerald-version/)
    - [Pokémon Ruby Version [save file] 2023-04-16](https://gbatemp.net/download/pokemon-ruby-version-save-file.37934/)
    - [Pokémon Emerald Version [save file] 2023-08-25](https://gbatemp.net/download/pokemon-emerald-version-save-file.38072/)
- gen4 在pal park
    - [SoulSilver ROM(JP)](https://www.emulatorgames.net/roms/nintendo-ds/pokemon-soul-silver-jp/)
    - [SoulSilver ROM(U)](https://www.emulatorgames.net/roms/nintendo-ds/pokemon-soulsilver-version/)
    - [Pokemon SoulSilver Version - Complete Save (100%) 1.1](https://gbatemp.net/download/pokemon-soulsilver-version-complete-save-100.38214/)

#### 绿宝石386 -> 原版绿宝石
原版没法读取魔改版存档，用修改器直接写内存（修改器原作者: Fuzzier(Gauchyler@etang.com) ）

## Reference
- 感觉是市面上最全的一个: [Guide: How to transfer a Pokemon through different generations using emulation](https://www.reddit.com/user/Porta_14/comments/lxbjwv/guide_how_to_transfer_a_pokemon_through_different/#:~:text=In%20your%20generation%204%20games,your%20save%20file%20as%20a%20%5B.)

- Might be interesting
    - [Trying Pal Park transfer from Pokemon Emerald to Pokemon Diamond on DeSmuME](https://gbatemp.net/threads/trying-pal-park-transfer-from-pokemon-emerald-to-pokemon-diamond-on-desmume.560355/)