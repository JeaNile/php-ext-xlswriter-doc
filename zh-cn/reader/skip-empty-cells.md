# 忽略空白单元格

* 读取文件暂不支持 `windows` 系统；
* 扩展版本大于等于 `1.2.7`；
* PECL 安装时将会提示是否开启读取功能，请键入 `yes`；

## 测试数据准备

```php
$config = ['path' => './tests'];
$excel  = new \Vtiful\Kernel\Excel($config);

// 写入测试数据
$filePath = $excel->fileName('tutorial.xlsx')
    ->header(['', 'Cost'])
    ->data([
        [],
        ['viest', '']
    ])
    ->output();
```

## 示例一

```php
// 读取全量数据
// 使用 \Vtiful\Kernel\Excel::SKIP_EMPTY_CELLS 忽略空白单元格
$data = $excel->openFile('tutorial.xlsx')
    ->openSheet('Sheet1', \Vtiful\Kernel\Excel::SKIP_EMPTY_CELLS)
    ->getSheetData();
```

## 示例二

```php
// 游标模式
// 使用 \Vtiful\Kernel\Excel::SKIP_EMPTY_CELLS 忽略空白单元格

$data = $excel->openFile('tutorial.xlsx')
    ->openSheet('Sheet1', \Vtiful\Kernel\Excel::SKIP_EMPTY_CELLS);

while ($data = $excel->nextRow()) {
    var_dump($data);
}
```