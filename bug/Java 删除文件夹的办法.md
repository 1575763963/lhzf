----		
title: Java 删除文件夹的办法		
tags: Java,删除,文件夹		
grammar_cjkRuby: true		
----		
		
  	File file = new File("D:/defonds/temp");  		
    		
 如果 "D:/defonds/temp" 是一个空目录的话，可以成功删除。但是如果是一个非空目录的话，就无法成功删除，必须将其子文件（目录）删除干净才可删除成功。使用以下的方法可以成功删除非空文件夹：		
 		
    public static void deleteFile(File file) {		
		if (file.exists()) {// 判断文件是否存在		
			if (file.isFile()) {// 判断是否是文件		
				file.delete();// 删除文件		
			} else if (file.isDirectory()) {// 否则如果它是一个目录		
				File[] files = file.listFiles();// 声明目录下所有的文件 files[];		
				for (int i = 0; i < files.length; i++) {// 遍历目录下所有的文件		
					FileUtil.deleteFile(files[i]);// 把每个文件用这个方法进行迭代		
				}		
				file.delete();// 删除文件夹		
			}		
		} else {		
			System.out.println("所删除的文件不存在");		
		}		
	}		
    		
 或者使用下边的这个方法，也很不错：		
 		
    public static void deleteAllFilesOfDir(File path) {  		
      if (!path.exists())  		
          return;  		
      if (path.isFile()) {  		
          path.delete();  		
          return;  		
      }  		
      File[] files = path.listFiles();  		
      for (int i = 0; i < files.length; i++) {  		
          deleteAllFilesOfDir(files[i]);  		
      }  		
      path.delete();  		
  }  
