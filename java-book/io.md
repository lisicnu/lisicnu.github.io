## File
### 文件读写相关
![](/images/file-1.png)

```
    public static void main(String[] args) {
        try {
            File f = new File("a.txt");
            FileOutputStream fop = new FileOutputStream(f);
            // 构建FileOutputStream对象,文件不存在会自动新建

            // 写文件
            OutputStreamWriter writer = new OutputStreamWriter(fop, "UTF-8");

            writer.append("中文输入");
            writer.append("\r\n");
            writer.append("English");

            writer.close();
            fop.close();

            // 读取文件内容
            FileInputStream fip = new FileInputStream(f);
            InputStreamReader reader = new InputStreamReader(fip, "UTF-8");

            StringBuffer sb = new StringBuffer();
            while (reader.ready()) {
                sb.append((char) reader.read());
            }
            System.out.println(sb.toString());
            reader.close();

            fip.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

```

## Diretory 相关
### 部分 API 说明#
- `mkdir()` 方法创建一个文件夹，成功则返回true，失败则返回false。失败表明File对象指定的路径已经存在，或者由于整个路径还不存在，该文件夹不能被创建。
- `mkdirs()`方法创建一个文件夹和它的所有父文件夹
- [测试题](./io-test.md)

## 控制台输入输出
- BufferedReader
- system.out.print()
- Scanner
