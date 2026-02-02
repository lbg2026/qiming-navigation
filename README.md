#启明导航页
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>启明导航页 - 智能优化版 | 含AA对话搜索+起点/笔阁趣</title>
    <!-- 核心安全头部配置 -->
    <meta http-equiv="X-Frame-Options" content="DENY">
    <meta http-equiv="X-XSS-Protection" content="1; mode=block">
    <meta http-equiv="X-Content-Type-Options" content="nosniff">
    <meta http-equiv="Referrer-Policy" content="no-referrer">
    <meta name="robots" content="noindex, nofollow">
    <!-- 外部资源：样式/图标/AI对话依赖 -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/axios@1.6.8/dist/axios.min.js"></script>
    <link rel="icon" href="https://img.icons8.com/fluent/48/4fc3f7/star-guide.png" type="image/png">
    <style>
        /* 基础样式重置 */
        *{margin:0;padding:0;box-sizing:border-box;}
身体{字体系列:“国际”, “微软雅黑”, 无衬线字体;背景:线性梯度(135（同degree）度，#0f172a0%，#1e293b100%);颜色:# e0e0e0行高:1.6;填料:20像素;最小高度:100vh;}
。容器{最大宽度:1400像素;边缘:0 汽车;}
        
        /* 头部样式 */
    header { text-align:center；边距-底部:30px填充:30px 0；border-bottom:1px solid rgba(79，195，247，0.2)；位置:相对；溢出:隐藏；}
    header::在{content:" "之前；位置:绝对；top:0；左:50%；transform:translate x(-50%)；宽度:60%；高度:2px背景:线性渐变(90度，透明，#4fc3f7，透明)；}
    页眉h1 { font-size:3 rem；颜色:# 4fc3f7边距-底部:10px字母间距:3px文字-阴影:0 0 15px rgba(79，195，247，0.3)；}
    页眉p { color:# 94a 3b 8；字体大小:1.1红色；边距-底部:15px}
    。安全提示{ display:inline-flex；对齐-项目:居中；差距:8px背景:rgba(30，41，59，0.8)；边框:1px纯色# 4fc3f7边框半径:30px填充:10px 20px边距-顶部:5px颜色:# 81c784字体大小:0.95雷姆；box-shadow:0 4px 15px rgba(0，0，0，0.3)；}
        
        /* 新增：AA对话搜索面板 */
    。ai-search-panel {背景:rgba(30，41，59，0.8)；边框:1px实心rgba(79，195，247，0.3)；边框半径:12px填充:25px边距-底部:30pxbox-shadow:0 4px 20px rgba(0，0，0，0.3)；背景-滤镜:模糊(10px)；}
    。ai-search-title { font-size:1.4 rem；颜色:# 4fc3f7边距-底部:20px显示器:flex对齐-项目：居中；差距:10px}
    。人工智能搜索框{ display:flex；差距:10pxflex-wrap:缠绕；}
    # ai-search-input { flex:1 1 80%；填充:15像素20像素背景:rgba(15，23，42，0.7)；边框:1px实心rgba(79，195，247，0.2)；边框半径:8px颜色:# e2e 8楼0字体大小:1雷姆；大纲：无；过渡：全0.3s}
    # ai-search-input:focus { border-color:# 4 fc3f 7；盒影:0 0 10px rgba(79，195，247，0.2)；}
    #人工智能-搜索-BTN { flex:1110%；最小宽度:100像素；填充:15像素20像素背景：线性梯度(135度、#4fc3f7 0%、# 2563 EB 100%)；边框：无；边框半径:8px颜色:# ffffont-size:1雷姆；光标：指针；过渡：全0.3秒显示器:flex对齐-项目：居中；对齐-内容:居中；差距:8px}
。ai-result-link { color:# 81c 784；文字-装饰：无；左边距:10px}
#ai搜索结果{ margin-top:20px；填充:20px背景:rgba(15，23，42，0.5)；边框半径:8px最小高度:80px显示器:flex对齐-项目：居中；对齐-内容：居中；颜色:# 94a 3 b 8字体大小:1雷姆；}
# ai-搜索-结果。正在加载{ color:# 4 fc3f 7；}
艾-搜索-结果has-result { color:# e2e 8 f 0；对齐-内容：灵活开始；align-items:flex-start；行高:1.8;}
。ai-result-item { margin-bottom:10px；填充-底部:10 px边框-底部:1px实心rgba(79，195，247，0.1)；}。ai-result-item { margin-bottom:10px；填充-底部:10 px border-bottom:1px solid rgba(79，195，247，0.1)；}
。人工智能搜索框{ display:flex；差距:10pxflex-wrap:缠绕；}
# ai-search-input:focus { border-color:# 4 fc3f 7；盒影:0 0 10px rgba(79，195，247，0.2)；}。ai-result-title { color:# 4 fc3f 7；字体粗细:600;}
。ai-result-link { color:# 81c 784；文字-装饰：无；左边距:10px}
。ai-result-link:hover { text-decoration:underline；}
        
        /* 信息面板样式 */
    。信息面板{显示：网格；网格-模板-列：重复（自动调整,最小最大(250px，1fr))；差距:20px边距-底部:30px}
    。信息卡{背景:rgba(30，41，59，0.7)；边框半径:12px填充:20pxbox-shadow:0 4px 20px rgba(0，0，0，0.3)；边框:1px实心rgba(79，195，247，0.1)；过渡：全0.3秒背景-滤镜：模糊(10px)；}
    。info-card:hover { transform:translate y(-5px)；盒影:0 8px 25px rgba(79，195，247，0.2)；边框颜色:rgba(79，195，247，0.3)；}
    。信息卡H3{字体大小:1.2雷姆；颜色:# 4fc3f7边距-底部:15px显示器:flex对齐-项目：居中；差距:10px}
    。信息卡I { font-size:1.5雷姆；颜色:# 81c784}
        
        /* 时间模块 */
    。time-module { text-align:center；}
    #当前时间{ font-size:3.5雷姆；字体粗细:700;颜色:# ffffff边距:10px 0；字母间距:2px}
    #当前日期{ font-size:1.1雷姆；颜色:# 94a3b8}
        
。人工智能搜索框{ display:flex；差距:10pxflex-wrap:缠绕；}    /* 天气模块 */
    。天气模块{ display:flex；伸缩方向：列；差距:10px}
    。天气标题{ display:flex；对齐-内容：空格-是吗
