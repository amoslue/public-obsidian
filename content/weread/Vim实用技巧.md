---
doc_type: weread-highlights-reviews
bookId: "729213"
author: Drew Neil
cover: https://cdn.weread.qq.com/weread/cover/34/YueWen_729213/t7_YueWen_729213.jpg
reviewCount: 1
noteCount: 4
readingStatus: 读过
progress: 8%
totalReadDay: 2
readingTime: 0小时29分钟
readingDate: 2020-08-17
isbn: 9787115338693
lastReadDate: 2020-08-18

---
# 元数据
> [!abstract] Vim实用技巧
> - ![ Vim实用技巧|200](https://cdn.weread.qq.com/weread/cover/34/YueWen_729213/t7_YueWen_729213.jpg)
> - 书名： Vim实用技巧
> - 作者： Drew Neil
> - 简介： Vim是程序员、网站开发人员及系统管理员的重要工具，其速度和效率令其他的文本编辑器难以望其项背。Vim能在几乎每一个系统上运行，并支持大多数编程语言和标记语言。《Vim实用技巧》包含了Vim的实用技巧和使用指南。全书概括了121个技巧，通过丰富的示例、清晰的体例和详细的讲解，展示了高效使用Vim的崭新方法。《Vim实用技巧》为那些想要提升自己的程序员编写，阅读本书是熟练地掌握高超的Vim技巧的必由之路。全书共21章，包括121个技巧。每一章都是关于某一相关主题的技巧集合。每一个技巧都有针对性地解决一个或一类问题，帮助读者提升Vim的使用技能。《Vim实用技巧》示例丰富，讲解清晰，采用一种简单的标记方法，表示交互式的编辑效果，可以帮助读者快速掌握和精通Vim。
> - 出版时间 2014-05-01 00:00:00
> - ISBN： 9787115338693
> - 分类： 计算机-计算机综合
> - 出版社： 人民邮电出版社
> - PC地址：https://weread.qq.com/web/reader/ce132a905b207dce166506f

# 高亮划线

## 第1章 Vim解决问题的方式

> 📌 合而为一
万事俱备！每次我们按 n 键时，光标就会跳到下一个“content”单词所在之处，而当我们按 . 键时，它就会把光标下的单词改为“copy”。
如果我们想替换所有地方，就可以不加思考地一直按 n.n.n. 以完成所有的修改（但是，这种情况下也可以用 :%s/content/copy/g 命令）。然而，由于我们需要留意不符合要求的匹配项，所以在按了 n 之后，我们要审视一下当前的匹配项，然后决定是否把它改为“copy”。如果需要修改的话，就按 . 命令，反之则不用。无论决定是什么，我们都可以再次按 n 移到下一个地方，如此循环往复，直到完成全部的修改。
技巧6 结识.范式
到目前为止，我们介绍了3个简单的编辑任务。尽管每个问题都不一样，不过我们都找到了用 . 命令解决该问题的方法。在本节，我们将对这些方案进行比较，并找出它们所共有的模式——一个我称之为“ . 
> ⏱ 2020-08-17 10:00:48 ^729213-9-10650

### 第2章 普通模式

> 📌 db 命令删除从光标起始位置到单词开头的内容， 
> ⏱ 2020-08-17 13:17:24 ^729213-11-3812-3835

> 📌 b 命令把光标移到单词的开头，移动好后，就可以用一个 dw 命令删掉整个单词。 
> ⏱ 2020-08-17 13:18:06 ^729213-11-4174-4213

> 📌 你可以把 daw 命令解读为“delete a word” 
> ⏱ 2020-08-17 13:19:14 ^729213-11-4636-4665

> 📌 <C-a> 和 <C-x> 命令分别对数字执行加和减操作。在不带次数执行时，它们会逐个加减，但如果带一个次数前缀，那么就可以用它们加减任意整数。例如，如果我们把光标移到字符5上，执行 10<C-a>就会把它变成15。 
> ⏱ 2020-08-18 02:03:30 ^729213-11-6095-6203

# 读书笔记

# 本书评论

## 书评 No.1 
妙啊，vim太强大了。 ^326477254-7jFBM3Jq3
⏱ 2020-08-17 10:00:33
