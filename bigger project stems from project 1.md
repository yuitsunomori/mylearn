# bigger project stems from project 1
- ## preface
  
  关于project1,空闲时仔细想了想，其实我真正想要构筑的是一种能够记录下我所思索的东西的application，这太过于笼统，我解释一下，如今有许多记录思绪的方式，做笔记，做思维导图，笔记可以进行各种引用（如果是电子笔记的话），思维导图能够更加直观的反映各个concept之间的关系。
  
  然而笔记多半只能线性地表示知识，并附以对应的理解，而且编制的过程十分麻烦，思维导图更是如此（laborious），而且往往不能cover许多内容。
  
  我想做的是一个能够实时记录下思绪的app，更准确地说，是能够“丰满地重现自己究竟是怎么想的”的app，或许不应当把他描述为一个记录软件，而是一种以机器为辅佐的思维方式，这整个对于某些特定主题进行联系性探究的的思考方式，而这种复杂的方式是纯粹的线性文字，或者树状的图是难以表示的，假若可以，也是十分繁杂而费力的工程。
  
  更具体地说，结合我的具体经验，无论是在学习数学和英语的时候，我有时会产生某种抓不到自己曾经研究过的事物的关键的感觉，即便当时十分投入（这也许与复习的规划有关，但是，复习又怎是一件易事呢？即便是第三天再次观看自己所做的笔记，仍旧感觉是重投来过，当然，或许重投来过或许是正常的，但是如果没有办法重投来过呢？如果没有一种工具帮助你记录你曾经意识到的某种关联性，如何能再一次观察那些概念的时候完美地复现那时的想法呢？记忆的隔阂让人沮丧，然而如果你能够无时无刻在学习时就记录下所有思绪，那当然很好，但是你怎么能保证这些联系被准确地记录了下来？因为学习的时间是连贯而前进的，行进时缺漏了哪一点都不奇怪）。
  
  在把一些概念放在一起比较或是构建一些联系时，思绪往往是四处分叉而且往往在深层的无意识与意识之间进行，然而并不是每一个关联性都是有效且重要的，而重要的关联却无时无刻发生着，散布在搜索（构建时，命名为surf，因为search是在surf下的一个个为了构建关联性的途径）的每一个角落，如果这些关联能快捷地统一地整理在一个软件当中，那么到某个时刻，需要寻回这些关联性与思路的时候，便能十分快速的通过某一个特殊地节点找到
  
  还有一个需要解决的问题，就是如何保证这种回溯的有效与高效性？
  
  
  
  
  
  
  
  关联性搜索其实一个很强大的工具就是gpt，从而，似乎将gpt嵌入这个软件是一个不错的选择，但是由于现在的我经济水平有限，可能无法实现这个功能（说不定哪天gpt-api免费了呢？）
  
  
  
  
  
  
  
  在背单词的时候产生的主要问题是，时时刻刻产生的联系性没有办法构筑成清晰的可以反复查看的形式，而这一过程日常中只能通过回去查看某一个单词，再去逐个观看每一个与其相关的词语的具体解释以及重新审视他们之间的区别。
  
  而需要实现的便捷性是，即使在每一个个体对象的知识解释界面中都能快速地引申出自己曾总结的与其他概念的相关（这包括的相关列表【包含了与这个对象所有的相关对象，并且以相关程度排列，或者是以别的标准形成的图或者排列】，以及各个关联对应的comment或explanation）
  
  而这些所有关联性的便捷性的构筑是为了让产生新的有意义的关联不再那么困难与曲折。（也许我也曾在本子上做过类似的关联性的事吧，比如把一大堆类似的词进行细致的分类，但是由于复习从来都是我的弱项，所以也没有进行很多这样的操作，主要是，时间太过有限，有时便捷性比能够理解到多深的能力重要的多）
  
  我觉得如果能够通过某个关键词对许多关联性组（由一个中心对象与许多关联对象组成的图）
  
  
  
  还有一个bullet point，关于中心对象的解释的问题，对于一类中心对象的理解是需要某种程度上的程式化的（或许对于某些学科不是），但是这都是从对中心对象本质的疑问而引申出来的，但无论如何，解释性的内容同样要体现某种对于理解的便捷性以及关联引导性。
-
-
- 对于完成背单词的工作，还有一点需要考虑，（思考至此，我觉得记忆是沉浸而且复杂的。统一性的时间，或者是人为管理的时间是不靠谱的，而且不够精确，故而，复习的计划以及时间线应当非线性的或者是差分的交给计算机处理），如果根据记忆曲线的记忆卡片能够在特定时间出现（如弹窗）。
-
- 作为计算机考试的准备，我决定先尝试一下这里的功能，然后有必要的时候自己做一些插件，由于logsseq是开源的，从而完成这个是可能的，只要补充相关gui的知识即可