# Ideal-Piano
这是一款智能钢琴软件，我在2020年的4月份开始开发，最近8月初接近完工。这款智能钢琴软件对于音乐初学者，音乐人，音乐爱好者等都有一些用处。 Ideal Piano最大的特色就是通过乐理逻辑的算法来判断当前演奏的音组成的是什么和弦，并且显示在屏幕上。这个算法是自己的一个项目， 乐理作曲语言库musicpy里面自己精心设计的一个乐理逻辑算法，判断的效果非常好，包括所有的原位和弦，各种和弦的转位，voicings 和变化音，省略音等等，可以判断非常覆杂的和弦组成，并且有多个乐理逻辑判断优先级的参数可以调整。 （默认的参数设置的适用性最广泛）

这个智能钢琴软件总共有三个模式，电脑键盘自由演奏，midi键盘自由演奏和播放midi文件分析和弦并且实时演示。在播放midi文件演示的模式中，可以选择通过算法去除主旋律，只听低音部分的和弦的音符。这三个模式在打开Ideal Piano之后选择左上角对应的按钮就可以进入。

第一个模式，电脑键盘自由演奏，默认的键位在config.py这个文件里，如果想要改变键盘对应的音符，直接在config.py里改然后保存即可。这个模式主要提供给没有任何midi键盘的小伙伴平时可以弹着玩（没错就是这么无聊www）

第二个模式，midi键盘自由演奏，接上midi键盘到电脑，然后进入这个模式，就可以在midi键盘上演奏，并且软件里同时会显示你当前弹的音在对应的钢琴的位置， 同时实时分析你当前弹下的音组成的是什么和弦（根音加上和弦类型的完整表述），并且显示在屏幕上。音源可以自己在config.py里设置路径和音源的文件类型 （wav, mp3, ogg等等）。之前我想实现同时DAW（编曲宿主）和Ideal Piano共用一个midi键盘，或者DAW里面播放工程同时Ideal Piano也可以显示当前的音符， 可是在一开始遭遇了失败，一直都是显示Host error之类的错误，后来我找到了很好的解决办法。 loopMIDI这个免费软件可以做到建立虚拟midi端口， 因此可以用来连接多个不同的软件的midi端口。使用loopMIDI可以让DAW和Ideal Piano同时使用一个midi键盘，这样你就可以在DAW里面加载自己想听的音源， 然后在midi键盘上演奏，听到的是DAW的音源，与此同时Ideal Piano也可以同步地实时显示当前演奏的和弦类型和音符。除此之外，也可以实现在DAW里播放工程， 同时Ideal Piano也可以显示当下演奏的和弦类型和音符。具体的操作流程我在“请先看我!.txt”里面写的很详细，请大家去看看。

第三个模式，播放midi文件实时分析当前的和弦，进入这个模式后，会弹出一个文件浏览框让大家选择想要在Ideal Piano里播放的midi文件，选择完成之后， 可以选择自己想要播放的midi轨道，选择播放的范围（按照百分比来算，比如播放前半段就可以输入在范围那边写0和50），也可以选择播放的BPM（曲速）。也可以选择通过算法去除主旋律，只听低音部分的和弦的音符。 （这个去除曲子的主旋律的算法是我自己想的，经过实测，对于大部分曲子的效果还是不错的） 这里需要特别说明的是，midi轨道那个框可以留空不用填，我写的程序会智能查找你选择的midi文件里的第一个有音符的轨道并且作为播放的轨道。因此如果是那种只有一个轨道的纯钢琴曲，那么就可以留空不用填，程序会直接播放那个有音符的轨道，如果是有多个轨道的midi，那么就根据自己的需要填入想要播放的轨道即可。在这个模式下，选择的midi文件会在Ideal Piano里播放，声音来自于自己设置好的音源（音源必须是一个文件夹里面是以音符为名字的音乐文件，比如C5.wav这种），在画面上会显示当前的音符在钢琴上的位置，并且实时分析当前演奏的音符组成的和弦。如果不想要声音来自于设置好的音源， 想要来自DAW的音源的话，使用loopMIDI就可以做到了，在DAW里播放工程，同时Ideal Piano可以同步接收到midi信号，实时分析当前的音符组成的和弦， 显示音符与和弦类型在屏幕上。具体的操作流程请到"请先看我!.txt"这个文件里看。

由于这个项目完全由本人一个人完成，本人的美工水平欠佳，因此只要不是对于美工很挑剔的话，Ideal Piano还是可以用的很顺畅的qwq

以下是Ideal Piano的画面预览：

![image](previews/1.jpg)

打开Ideal Piano的初始页面

![image](previews/2.jpg)

演奏时显示音符并且实时通过乐理逻辑分析判断当前演奏的音组成的和弦类型

![image](previews/3.jpg)

选择midi文件播放的窗口


其他的说明：

1. 好像有些人github下载失败，所以我坚果云也传了一份，直接可以下载（不用注册） https://www.jianguoyun.com/p/DUbKo0UQhPG0CBjHwbID

2. 由于我这个软件是全英文的，考虑到很多小伙伴可能看中文的和弦类型名称比较亲切一些，因此我做了一个中文补丁包，变成中文的内容包括：界面的按钮，
显示的和弦种类名称，（原位和弦会保留其他的英文称呼，第一个是中文名称），单音和音程，选择midi文件的界面和每个设置项，更改设置的程序。
中文补丁安装包的下载地址：https://www.jianguoyun.com/p/DabhR74QhPG0CBi3vrID

3. 默认的和弦显示对齐模式已经更新为左对齐，取代原来的居中显示，看着更舒服，避免了实时分析中和弦名长度不断变化导致眼睛跟不上的情况。

4. 最近加入了音符条模式，之前只有音符点显示在钢琴键位上的模式，这次加入的音符条模式相对来说更有欣赏价值一些。音符从键位出现并且上升，无论是自己演奏还是播放midi文件都是这样。
自己演奏时如果按着不放，音符条就会一直拉长，放开之后音符条就会为往上飘。播放midi文件则是直接根据每个音符的长度算出音符条的相对长度。而且音符的力度对应到了音符的透明度，（这个
功能可以在设置文件里对应的参数设置开或关）然后还可以选择出现单色或者随机任意颜色，效果还是不错的。现在这个音符条的模式(bars)作为和之前的音符点(dots)一起存在的两种模式，可以
在设置文件里自己设置想要哪种模式。音符的出现位置，音符的长度和宽度，音符每次上升走的步数（走多少个像素），音符的颜色，单色显示或者随机显示颜色，音符的默认透明度，音符的拉长速
度等等都可以在config.py里进行设置。

5. 这个软件的各种参数设置都可以到config.py里去修改，保存之后再打开软件就可以看到变化了。

如果有遇到任何问题，请加我的qq号2180502841来跟我说，感谢大家的支持~

这个软件在实时和弦判断用到的乐理逻辑算法来自于我的另一个项目，专业乐理作曲语言musicpy里我精心设计的一个和弦判断的算法，

完全按照乐理的逻辑来推测。在播放midi的模式下可以选择去除主旋律，这个去除主旋律的算法也同样来自我的项目musicpy，

所以可以说这个智能钢琴软件就是musicpy的其中一个实际应用。对musicpy这个项目感兴趣的欢迎来看我的repository，链接在这里

https://github.com/Rainbow-Dreamer/musicpy


最近收到的反馈中有不少觉得原来的默认字体Comic Sans MS很不正式，因此我现在换成了Cambria这个字体，看起来正式了很多，我也把默认字体大小和按钮大小都调大了。

现在的音符条模式下看起来是这样的：

![image](previews/4.jpg)

![image](previews/5.jpg)
