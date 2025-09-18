# eeed-editor —— 基于 Tiptap 与 Vue 3 开发的现代化富文本编辑器

## 特性

1. 基本功能：撤销、格式刷、字体、标题、文字大小、文字颜色、文字背景色、粗体、斜体、下划线、删除线、引用、行内代码、分割线、有序列表、无序列表、任务列表、布局、行高、缩进、表格、插入图片
2. 高级功能
  - 数学公式插入、渲染、修改
  - 大模型输出内容复制过来完整格式渲染
  - Mermaid渲染
  - 导出word
3. 多种布局方式，适配各种富文本编辑器使用场景
  - A4模式
  - defaultA4模式
  - default模式
4. 适用场景
  - 全屏文档编辑器
  - 小区域编辑器
  - 大模型问答结果输出渲染

# 使用
```vue
<template>
  <eeedEditor :config="defaultConfig" :title="title" :content="content" :onUploadFile="handleUploadFile" :onSave="handleSave" :onChange="handleChange"/>
</template>

<script setup>
import eeedEditor from "eeed-editor";
import "eeed-editor/dist/index.css";
const title = ref("标题") // 编辑器标题
const content = ref("内容"); // 编辑器内容
const defaultConfig = {
  mode: "doc",
  editable: true, // 设置为false表示只读模式，设置为false之后，doc参数中参数可无需设置
  doc: {
    page: {
      mode: "A4",
      style: {
        position: "absolute",
        backgroundColor: "#f5f5f5",
      },
    },
    headerBar: {
      visible: true,
      home: {
        visible: true,
        icon: "back",
        path: "/",
      },
      export: {
        visible: true,
      },
      title: {
        visible: true,
      },
    },
    toolBar: {
      visible: true,
      align: "center",
    },
  },
} as const;

// 上传文件
const handleUploadFile = (file: File) => {
  return new Promise<string>((resolve, reject) => {
    console.log("开始上传文件：", file.name);

    // 模拟异步上传
    setTimeout(() => {
      // 假设上传成功
      const uploadedUrl = `https://xxxxxxxxxxxxxx.png`;
      console.log("上传成功，文件 URL：", uploadedUrl);
      resolve(uploadedUrl);
    }, 1500);
  });
};


// 保存
const handleSave = (title: string, content: string) => {
  console.log(title, content);
};

// 内容改变
const handleChange = (htmlContent: string, textContent: string) => {
  console.log(htmlContent, textContent);
};
<script>
```

有问题加我微信zmx119966
