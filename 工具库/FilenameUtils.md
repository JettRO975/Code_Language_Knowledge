---
tags:
  - Java
  - FilenameUtils
---

# FilenameUtils（文件名/后缀名相关）

FilenameUtils.concat(String basePath, String fullFilenameToAdd) // 合并目录和文件名为文件全路径

FilenameUtils.getBaseName(String filename) // 去除目录和后缀后的文件名

FilenameUtils.getExtension(String filename) // 获取文件的后缀

FilenameUtils.getFullPath(String filename) // 获取文件的目录

FilenameUtils.getName(String filename) // 获取文件名

FilenameUtils.getPath(String filename) // 去除盘符后的路径

FilenameUtils.getPrefix(String filename) // 盘符

FilenameUtils.indexOfExtension(String filename) // 获取最后一个.的位置

FilenameUtils.indexOfLastSeparator(String filename) // 获取最后一个/的位置

FilenameUtils.normalize(String filename) // 获取当前系统格式化路径

FilenameUtils.removeExtension(String filename) // 移除文件的扩展名

FilenameUtils.separatorsToSystem(String path) // 转换分隔符为当前系统分隔符

FilenameUtils.separatorsToUnix(String path) // 转换分隔符为linux系统分隔符

FilenameUtils.separatorsToWindows(String path) // 转换分隔符为windows系统分隔符

FilenameUtils.equals(String filename1, String filename2) // 判断文件路径是否相同，非格式化

FilenameUtils.equalsNormalized(String filename1, String filename2) // 判断文件路径是否相同，格式化

FilenameUtils.directoryContains(String canonicalParent, String canonicalChild) // 判断目录下是否包含指定文件或目录

FilenameUtils.isExtension(String filename, String extension) // 判断文件扩展名是否包含在指定集合(数组、字符串)中

FilenameUtils.wildcardMatch(String filename, String wildcardMatcher) // 判断文件扩展名是否和指定规则匹配

## 相关笔记

- [[FileUtils]]

