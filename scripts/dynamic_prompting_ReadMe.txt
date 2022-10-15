动态提示模板
AUTOMATIC1111/stable-diffusion-webui的自定义脚本，用于实现用于随机提示生成的微型模板语言。

使用此脚本，提示：

A {house|apartment|lodge|cottage} in {summer|winter|autumn|spring} by {2$$artist1|artist2|artist3}
会出现以下任何提示：

夏天的房子，艺术家 1 ,艺术家2
秋天的小屋，艺术家 3 ,艺术家1
冬天的小屋，艺术家 2 ,艺术家3
...
如果您正在搜索艺术家和风格的有趣组合，这将特别有用。

您还可以从文件中选择一个随机字符串。假设您在 WILDCARD_DIR 中有文件 seasons.txt（见下文），则：

__seasons__ is coming
可能会生成以下内容：

冬天来了
春天来了
...
您还可以使用相同的通配符两次

I love __seasons__ better than __seasons__
我爱冬天胜过夏天
我爱春天胜过春天
模板语法
组合
{2$$opt1|opt2|opt3}
这将随机组合每个批次的两个选项，用逗号分隔。在这种情况下，“opt1，opt2”或“opt2，opt3”，或“opt1，opt3”或相反顺序的相同对。

前缀2$$可以使用介于 1 和您定义的选项总数之间的任何数字。如果省略大小前缀，则使用 1

通配符文件
此脚本不提供通配符文件，因为列表存在于其他存储库中。一个开始寻找的好地方就在这里

嵌套
您可以在通配符内嵌套组合。这意味着您可以创建更高级的模板。例如：

{__seasons__|__timeofday__}
然后，这将从 seasons.txt 中选择一个季节，或者从 timeofday.txt 中选择一个时间。

WILDCARD_DIR
该脚本在 WILDCARD_DIR 中查找通配符文件。这是在 wildcard_dir 下的主 webui config.json 中定义的。如果 wildcard_dir 缺失，那么通配符文件应该放在 scripts/wildcards/