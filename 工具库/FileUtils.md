---
tags:
  - Java
  - FileUtils
---

# 2，FileUtils（文件/文件夹相关）

## 复制文件夹

FileUtils.copyDirectory(File srcDir, File destDir) // 复制文件夹（文件夹里面的文件内容也会复制）

FileUtils.copyDirectory(File srcDir, File destDir, FileFilter filter) // 复制文件夹，带有文件过滤功能

FileUtils.copyDirectoryToDirectory(File srcDir, File destDir) // 以子目录的形式将文件夹复制到到另一个文件夹下



## 复制文件

FileUtils.copyFile(File srcFile, File destFile) // 复制文件

FileUtils.copyFile(File input, OutputStream output) // 复制文件到输出流

FileUtils.copyFileToDirectory(File srcFile, File destDir) // 复制文件到一个指定的目录

FileUtils.copyInputStreamToFile(InputStream source, File destination) // 把输入流里面的内容复制到指定文件

FileUtils.copyURLToFile(URL source, File destination) // 把URL 里面内容复制到文件(可以下载文件)

FileUtils.copyURLToFile(URL source, File destination, int connectionTimeout, int readTimeout)



## 把字符串写入文件

FileUtils.writeStringToFile(File file, String data, String encoding)

FileUtils.writeStringToFile(File file, String data, String encoding, boolean append)

## 把字节数组写入文件

FileUtils.writeByteArrayToFile(File file, byte[] data)

FileUtils.writeByteArrayToFile(File file, byte[] data, boolean append) FileUtils.writeByteArrayToFile(File file, byte[] data, int off, int len) FileUtils.writeByteArrayToFile(File file, byte[] data, int off, int len, boolean append)



## 把集合里面的内容写入文件

// encoding：文件编码，lineEnding：每行以什么结尾

FileUtils.writeLines(File file, Collection<?> lines)

FileUtils.writeLines(File file, Collection<?> lines, boolean append)

FileUtils.writeLines(File file, Collection<?> lines, String lineEnding)

FileUtils.writeLines(File file, Collection<?> lines, String lineEnding, boolean append)

FileUtils.writeLines(File file, String encoding, Collection<?> lines)

FileUtils.writeLines(File file, String encoding, Collection<?> lines, boolean append)

FileUtils.writeLines(File file, String encoding, Collection<?> lines, String lineEnding)

FileUtils.writeLines(File file, String encoding, Collection<?> lines, String lineEnding, boolean append)



## 往文件里面写内容

FileUtils.write(File file, CharSequence data, Charset encoding)

FileUtils.write(File file, CharSequence data, Charset encoding, boolean append)

FileUtils.write(File file, CharSequence data, String encoding)

FileUtils.write(File file, CharSequence data, String encoding, boolean append)



## 文件移动

FileUtils.moveDirectory(File srcDir, File destDir) // 文件夹在内的所有文件都将移动FileUtils.moveDirectoryToDirectory(File src, File destDir, boolean createDestDir) // 以子文件夹的形式移动到另外一个文件下

FileUtils.moveFile(File srcFile, File destFile) // 移动文件

FileUtils.moveFileToDirectory(File srcFile, File destDir, boolean createDestDir) // 以子文件的形式移动到另外一个文件夹下

FileUtils.moveToDirectory(File src, File destDir, boolean createDestDir) // 移动文件或者目录到指定的文件夹内



## 清空和删除文件夹

FileUtils.deleteDirectory(File directory) // 删除文件夹，包括文件夹和文件夹里面所有的文件

FileUtils.cleanDirectory(File directory) // 清空文件夹里面的所有的内容

FileUtils.forceDelete(File file) // 删除，会抛出异常

FileUtils.deleteQuietly(File file) // 删除，不会抛出异常



## 创建文件夹

FileUtils.forceMkdir(File directory) // 创建文件夹(可创建多级)

FileUtils.forceMkdirParent(File file) // 创建文件的父级目录



## 获取文件输入/输出流

FileUtils.openInputStream(File file)

FileUtils.openOutputStream(File file)

## 读取文件

FileUtils.readFileToByteArray(File file) // 把文件读取到字节数组

FileUtils.readFileToString(File file, Charset encoding) // 把文件读取成字符串

FileUtils.readFileToString(File file, String encoding)

FileUtils.readLines(File file, Charset encoding) // 把文件读取成字符串集合

FileUtils.readLines(File file, String encoding)



## 测试两个文件的修改时间

FileUtils.isFileNewer(File file, Date date)

FileUtils.isFileNewer(File file, File reference)

FileUtils.isFileNewer(File file, long timeMillis)

FileUtils.isFileOlder(File file, Date date)

FileUtils.isFileOlder(File file, File reference)

FileUtils.isFileOlder(File file, long timeMillis)





## 文件/文件夹的迭代

FileUtils.iterateFiles(File directory, IOFileFilter fileFilter, IOFileFilter dirFilter)

FileUtils.iterateFiles(File directory, String[] extensions, boolean recursive)

FileUtils.iterateFilesAndDirs(File directory, IOFileFilter fileFilter, IOFileFilter dirFilter)

FileUtils.lineIterator(File file)

FileUtils.lineIterator(File file, String encoding)



FileUtils.listFiles(File directory, IOFileFilter fileFilter, IOFileFilter dirFilter)

FileUtils.listFiles(File directory, String[] extensions, boolean recursive)

FileUtils.listFilesAndDirs(File directory, IOFileFilter fileFilter, IOFileFilter dirFilter)



## 其他

FileUtils.isSymlink(File file) // 判断是否是符号链接

FileUtils.directoryContains(File directory, File child) // 判断文件夹内是否包含某个文件或者文件夹

 FileUtils.sizeOf(File file) // 获取文件或者文件夹的大小

FileUtils.getTempDirectory()// 获取临时目录文件

FileUtils.getTempDirectoryPath()// 获取临时目录路径

FileUtils.getUserDirectory()// 获取用户目录文件

FileUtils.getUserDirectoryPath()// 获取用户目录路径

FileUtils.touch(File file) // 创建文件

FileUtils.contentEquals(File file1, File file2) // 比较两个文件内容是否相同

## 相关笔记

- [[File]]
- [[IO流]]

