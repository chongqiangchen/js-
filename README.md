## 1. delay，延迟
```
export const delay = ms => new Promise(resolve => setTimeout(resolve, ms));
```

#### 应用：
```
*download*
export const download = async (url) => {
  const a = document.createElement('a');
  a.href = url;
  a.style.display = 'none';
  document.body.append(a);
  a.click();

  await delay(100);
  a.remove();
};

*batch download*
export const batchDownload = async (urls) {
  for (const url of urls) {
    // 可加一些类型校验
    await delay(100);
    download(url);
  }
}
```

## 2. 利用 `,` 切割数字
```
export const formatNumber = (num)=>{
  return num.replace(/(\d)(?=(\d{3})+$)/g, '$1,')
}
```

