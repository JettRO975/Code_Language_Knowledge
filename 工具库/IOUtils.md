---
tags:
  - Java
  - IOUtils
---

# 1，IOUtils（数据相关）

## 拷贝方法：

copy方法有多个重载方法，满足不同的输入输出流

IOUtils.copy(InputStream input, OutputStream output)

IOUtils.copy(InputStream input, OutputStream output, int bufferSize)//可指定缓冲区大小

IOUtils.copy(InputStream input, Writer output, String inputEncoding)//可指定输入流的编码表

IOUtils.copy(Reader input, Writer output)

IOUtils.copy(Reader input, OutputStream output, String outputEncoding)//可指定输出流的编码表



## 拷贝大文件的方法：

// 这个方法适合拷贝较大的数据流，比如2G以上

IOUtils.copyLarge(Reader input, Writer output) // 默认会用1024*4的buffer来读取

IOUtils.copyLarge(Reader input, Writer output, char[] buffer)//可指定缓冲区大小



## 将输入流转换成字符串

IOUtils.toString(Reader input)

IOUtils.toString(byte[] input, String encoding)

IOUtils.toString(InputStream input, Charset encoding)

IOUtils.toString(InputStream input, String encoding)

IOUtils.toString(URI uri, String encoding)

IOUtils.toString(URL url, String encoding)



## 将输入流转换成字符数组

IOUtils.toByteArray(InputStream input)

IOUtils.toByteArray(InputStream input, int size)

IOUtils.toByteArray(URI uri)

IOUtils.toByteArray(URL url)

IOUtils.toByteArray(URLConnection urlConn)

IOUtils.toByteArray(Reader input, String encoding)



## 字符串读写

IOUtils.readLines(Reader input)

IOUtils.readLines(InputStream input, Charset encoding)

IOUtils.readLines(InputStream input, String encoding)

IOUtils.writeLines(Collection<?> lines, String lineEnding, Writer writer)

IOUtils.writeLines(Collection<?> lines, String lineEnding, OutputStream output, Charset encoding)

IOUtils.writeLines(Collection<?> lines, String lineEnding, OutputStream output, String encoding)





## 从一个流中读取内容

IOUtils.read(InputStream input, byte[] buffer)

IOUtils.read(InputStream input, byte[] buffer, int offset, int length) IOUtils.read(Reader input, char[] buffer)

IOUtils.read(Reader input, char[] buffer, int offset, int length)





## 把数据写入到输出流中

IOUtils.write(byte[] data, OutputStream output)

IOUtils.write(byte[] data, Writer output, Charset encoding)

IOUtils.write(byte[] data, Writer output, String encoding)

IOUtils.write(char[] data, Writer output)

IOUtils.write(char[] data, OutputStream output, Charset encoding)

IOUtils.write(char[] data, OutputStream output, String encoding)

IOUtils.write(String data, Writer output)

IOUtils.write(CharSequence data, Writer output)



## 从一个流中读取内容，如果读取的长度不够，就会抛出异常

IOUtils.readFully(InputStream input, int length)

IOUtils.readFully(InputStream input, byte[] buffer)

IOUtils.readFully(InputStream input, byte[] buffer, int offset, int length) IOUtils.readFully(Reader input, char[] buffer)

IOUtils.readFully(Reader input, char[] buffer, int offset, int length)



## 比较

IOUtils.contentEquals(InputStream input1, InputStream input2) // 比较两个流是否相等

IOUtils.contentEquals(Reader input1, Reader input2)

IOUtils.contentEqualsIgnoreEOL(Reader input1, Reader input2) // 比较两个流，忽略换行符



## 其他方法

IOUtils.skip(InputStream input, long toSkip) // 跳过指定长度的流

IOUtils.skip(Reader input, long toSkip)

IOUtils.skipFully(InputStream input, long toSkip) // 如果忽略的长度大于现有的长度，就会抛出异常

IOUtils.skipFully(Reader input, long toSkip)

## 相关笔记

- [[IO流]]

