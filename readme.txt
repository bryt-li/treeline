Jeff's modification:
#####################################################

. 全部修改在1.4.1版本基础上进行

. 增加了tts的菜单项并调用node workspace/tts/run.js来处理语音合成


. 增加了导出原始输出为纯文本文件的功能，目前主要用于生成各种格式的文本文件
example:
treeline --export-rawoutput in.trl --outfile=out.trl

. 在输出rawoutput时，增加了输出子节点内容的功能，使用以下tag输出子节点内容：
{*DescendantOutput*}
example:
treeline --export-rawoutput in.trl --outfile=out.trl

. 在输出rawoutput时，增加了指定外部trl文件作为输出模板的功能
--tplfile=
example:
treeline --export-rawoutput in.trl --tplfile=template.trl --outfile=out.trl

. 在输出rawoutput时，增加了仅输出指定title的结点的功能，可指定多个结点名称（用逗号分隔），如不指定则默认输出root结点
--rootnode=
example:
treeline --export-rawoutput in.trl --rootnode=第一节概述,结论 --outfile=out.trl

. 模仿fieldformat.py中PictureFormat的方法，新增一个类FileFormat，实现了新的字段类型FieldType:File，用于输出文本文件的内容





Todo:
################################################
. 增加-y --type参数，仅显示TypeSetDlg，编辑结点类型
treeline -y foo.trl







Bugs:
################################################
使用命令行无法正确输出{*!File_Path*}之类的标签，因为这类标签值的初始化在globalref里，而命令行没有调用界面，而后者才初始化了globalref里的相应值
