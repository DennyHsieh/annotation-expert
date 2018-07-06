# Dataset of Music Annotation by Experts
The annotation files are the dataset containing tables of data relating to songs which are annotated by experts whose background is related to music.

## SOP of Annotation

**Getting Started**

- Sonic Visualiser [下載](https://www.sonicvisualiser.org/download.html)

**Procedures**

- Step 1: 選擇上方選單File > Open > 選取歌曲，或是拖曳檔案，將歌曲加載到Sonic Visualiser，此時會顯示歌曲波形。
![](https://github.com/DennyHsieh/annotation-expert/image/annotation_1.png)

- Step 2:  選擇上方選單 Pane > Add New Pane 或快捷鍵 N 產生一個新的標記面板。此時若按分號鍵 (***;***) 會在黑色豎槓處產生一個標記 (Time Instants Layer) 。
![](https://github.com/DennyHsieh/annotation-expert/image/annotation_2.png)

- Step 3: 按下播放(或空白鍵)並聆聽音樂，並在欲標記處按下分號鍵 (*;*) 以作標記。如果錯過的話，可按暫停播放(或再一下空白鍵)並拖移音軌至欲標記處，重新做標記。按ctrl+z (mac: command + z) 可以退回上一步。
- Step 4: 整首歌標記完後，選擇上方選單 Layer > Edit Layer Data 或按快捷鍵E打開圖層數據編輯視窗 (Data Editor)，將打開一個新視窗。第一欄為時間 (已自動轉換為秒)，在第三欄輸入標記的文字敘述 (例如 intro, verse, chorus, bridge等等。)
![](https://github.com/DennyHsieh/annotation-expert/image/annotation_3.png)

- Step 4: 標記的格式為

| Time | Frame  | Label |
| ---- | ------ | ----- |
| 開始時間 | (自動帶出) | 標記名稱  |
| 結束時間 | (自動帶出) | 標記名稱  |

- Step 5: 標記項目、順序與說明如下，詳細說明在[Lable Help](/doc/Dataset-of-Music-Annotation-by-Experts-6ZL1Zs2K2wP2Dqbg8FzE5#:h2=Lable-Help)

| 順序  | 項目(layer)                    | 標記(Lable)                                                                                                  | 說明                                                                                                                      |
| --- | ---------------------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 1st | **特別標記**(**Special labels)** | silence, end                                                                                               | - 標記音檔起始空白為silence、音樂結束點為silence、整個音檔最後一秒為end
- 將音軌拖移至左方音樂起始處，按分號鍵打上第一個標記 silence。拖移至右方音樂停止處，按分號鍵打上標記 end。（此二標記為必須之標記。） |
| 2nd | **結構(Structure)**            | intro, verse, chorus, inter, bridge, outro                                                                 | 標記出音樂架構中每個段落的起始及結束                                                                                                      |
| 3rd | **樂句(Melody-based Phrase)**  | 無                                                                                                          | 標記出每個樂句起始處                                                                                                              |
| 4th | **歌詞句(Cadence)**             | **A:** Authentic (V-I),
**P:** Plagal (IV-I),
**H:** Half (-V),
**D:** Deceptive (V-x, x=ii、IV6、iv6、vi、VI) | 有用到此四個終止式即標記，標註在該終止式"**結束的時間點**"，例如V-I，就標 I 結束的時間點(因為那才是一個"分界")，然後label就標是哪一種終止式                                        |
| 5th | 歌詞句(**Lyric-based Phrase**)  | 無                                                                                                          | - 標記出每句歌詞起始處
- (結束??需要譜)                                                                                                |


![](https://github.com/DennyHsieh/annotation-expert/image/annotation_toc.png)



- Step 6: 存檔方式
  - 選擇 File > Export Annotation Layer 以儲存 Annotation 檔案，檔案格式為 .csv。
  - 每個大項目開一新的 Pane (Pane > Add New Pane) 做標記，各別存成一個檔。
  - 資料夾名稱：歌名-流水號, song_id-流水號
    - 0000000-零距離-1, 0000000-1
    - 流水號1-3
  - 檔名取法：歌名-項目-流水號.csv
    - 歌名：“song_id-song_name.mp3”
    - ex: 當歌名為 star.mp3時，歌曲ID為1000時，最後會輸出如下的檔案
      - 0001000-star-special.csv
      - 0001000-star-structure.csv
      - 0001000-star-melodyPhrase.csv
      - 0001000-star-cadence.csv
    - 歌詞句以KKBOX所提供歌詞修改，以儲存 Annotation 檔案，檔案格式為 .csv。
      - 0001000-star-lyricPhrase.csv
    - 再選擇 File > Save Session As 以儲存工作檔，並將檔名存成與歌名相同、檔案格式為 .sv。
      - 0001000-star.sv

**Lable Help**

- 結構標示方法
  - 連續結構：Structure, Melody-based Phrase，只標起始，並於最後一個
  - 不連續結構：Cadence, Lyric-based Phrase，需標頭尾(-V只需標尾)
  - 特別標記：Special labels
- 標記格式
  - Example 1：某首歌的 61秒至76秒為Bridge，76秒至106秒為Chorus，則標記如下：
| Time     | Frame | Label        |
| -------- | ----- | ------------ |
| 1:01.000 | xxx   | Bridge start |
| 1:16.000 | xxx   | Chorus start |
| 1:46.000 | xxx   | Chorus end   |



- Example 2：某首歌的61秒至76秒為歌詞句A，81秒至111秒為歌詞句B，則標記如下：
| Time     | Frame | Label   |
| -------- | ----- | ------- |
| 1:01.000 | xxx   | A       |
| 1:16.000 | xxx   | A       |
| 1:21.000 | xxx   | B-start |
| 1:51.000 | xxx   | B-end   |



- 結構(Structure)標記說明
  - 前奏 (intro)：在一首歌開頭，導引出整首曲子。
  - 前導主歌(pre-verse)：在前奏與主歌之間，導引出主歌的片段。(這部份我們沒分那麼細)不分的話，需要討論是要歸到verse還是others還是intro。其實分出來會比較方便一點。
    - 例1：新寶島康樂隊〈鼓聲若響〉主歌開始前三小節
    - 例2：Queen "Bohemian Rhapsody" 主歌開始前二小節
  - 主歌 (verse)：通常主歌會在樂曲中重複，相較於副歌，主歌的歌詞較容易在每一次重覆時變化。
  - 前導副歌 (pre-chorus)：在主歌與副歌之間，導引出副歌的片段。(這部份我們沒分那麼細)前導副歌是很常見的，建議特別分類。前導主歌可以不用分出來沒關係。OK，那我再增加此部分DEMO
    - 例1：陳奕迅〈十年〉副歌開始前八小節
    - 例2：
  - 副歌 (chorus)： 一首歌中最被強調、重複最多的片段。
  - 間奏 (inter)：通常指副歌結束到下一次主歌前面的片段。
  - 橋段 (bridge)：導引出最後一次主歌/副歌的片段，可以是人聲也可以是樂器solo。
    - 例子：戴愛玲〈對的人〉最後一次副歌開始前八小節
  - 尾奏 (outro)： 歌曲最後結束一首歌的片段。
  - 其他 (others)：自成一段但無法分的，如暫停(break)、刻意的延長(suspension)、無音樂進行之對話、環境聲等等。
  - 注意事項：
    - 並非每一首歌都擁有上述的每一項。例如若該首曲子沒有前奏，便不需要標。
    - 有時候前奏其實是用副歌的旋律(例：五月天〈你不是真正的快樂〉)
    - 有時候主歌與主歌之間有間奏(例：孫燕姿〈遇見〉頭兩次主歌之間三小節多)
- 歌詞句標記範例
  - Ex.1
  > /還記得我們曾經 肩並肩一起走過 那段繁華巷口
  > /儘管你我是陌生人 是過路人
  > /但彼此還是感覺到了對方的 一個眼神 一個心跳.... 一種意想不到的快樂
  > /好像是 一場夢境
  > /命中註定/


  - Ex.2
  > /感傷的距離 有了思念而分開
  > /快樂的距離 是你永遠在我身旁
  > /有多少公里 才能築成完整愛情
  > /距離別讓我們分開

**Demo**
若想參考demo檔，請下載demo資料夾，並將示範音樂下載成mp3檔，將音樂檔命名為"0000000-零距離.mp3"後移動到demo資料夾內。

- 示範檔案：https://github.com/DennyHsieh/annotation-expert/demo
- 示範音樂：https://www.youtube.com/watch?v=94SsKt8p5jA
- 示範和弦譜：http://www.guitar-score.tw/2012/07/double-2.html, https://github.com/DennyHsieh/annotation-expert/image/0000000-零距離-chord.jpg

**Problem**

1. 刪除樂器
2. 連續標記之部分 Structure, MelodyPhrase (1)只標起始 (2)結束判斷
3. 不連續標記A-start, A-end，或是每2個A一組?
4. 歌詞句不好標
5. pre-verse, pre-chorus定義?
6. 檔名命名? ID?KKBOXid?song name?因為同首歌有3人標，0001000-star-Structure.csv or 0001000-star-Structure-1.csv
7. 資料夾命名(在annotation_expert資料夾底下) 0000000-零距離-1, 0000000-1
8. LyricPhrase需要KKBOX歌詞，目前只標開始未標結束，Cadence需要譜

**Reference**

- Sonic Visualiser [3.0.3 版本說明檔](https://sonicvisualiser.org/doc/reference/3.0/en/index.html)
  - 特別注意[Time Instants Layer](https://sonicvisualiser.org/doc/reference/3.0/en/index.html#timeinstants)（第6.5節）和 [Annotation by Tapping](https://sonicvisualiser.org/doc/reference/3.0/en/index.html#tapping) 的說明（第10節）
- [SALAMI annotation guide](http://www.music.mcgill.ca/~jordan/salami/SALAMI-Annotator-Guide.pdf)
## List of Tables

To be completed


## Note

Example 6-1

> /別想太多 沒有誰是誰的英雄
> /別再求救 在愛情裡 沒有誰對誰錯
> /發送訊號 就能在空中感受你的擁抱
> /一個問號 成了撲朔迷離的代表
> /遙遠的距離 隱藏自由的秘密
> /最近的距離 就像不完美的美麗
> /有多少公里 才能築成完整愛情
> /我們之間零距離/
> /兩個城市 寫滿多少想念的文字
> /多作解釋 只是徒勞無功的方式
> /只要一片星空 就能證明彼此的存在
> /好久不見 卻是噓寒問暖的鑰匙
> /遙遠的距離 隱藏自由的秘密
> /最近的距離 就像不完美的美麗
> /有多少公里 才能築成完整愛情
> /我們之間零距離
> /感傷的距離 有了思念而分開
> /快樂的距離 是你永遠在我身旁
> /有多少公里 才能築成完整愛情
> /距離別讓我們分開
> 距離你快點走開
> /我們之間 零距離/
