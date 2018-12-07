# 导出excel表格方式
1.给出excel地址,直接使用window.open('地址');或者location.href='地址';
2.后台返回数据流的形式，前端处理;
```
if (data.type == 'application/json') {
    let reader = new FileReader()
    reader.readAsText(data)
    reader.onload = () => {
        let obj = JSON.parse(reader.result)
        this.$message.error(obj.errorMsg || '网络异常，请稍后再试！')
        };
    return false
};
let text = '松鹤楼券码报表' + new Date().toLocaleDateString()
let url = window.URL.createObjectURL(new Blob([data]))
let link = document.createElement('a')
link.style.display = 'none'
link.href = url
link.setAttribute('download', `${text}.xlsx`)
document.body.appendChild(link)
link.click()
```