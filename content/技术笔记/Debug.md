
## maven找不到java_home解决方案：

The `JAVA_HOME` environment variable is typically needed by Maven to locate the Java installation on your system. If you encounter the error message "The JAVA_HOME environment variable is not defined correctly," it means that Maven cannot find the correct Java installation.

To resolve this issue, you can follow these steps to set the `JAVA_HOME` environment variable:

1. Determine the path to your Java installation. By default, Java is installed in `/Library/Java/JavaVirtualMachines/`.

2. Open Terminal and run the following command to find the latest installed Java version:

   ```
   /usr/libexec/java_home
   ```

   This command will display the path to the latest installed Java version.

3. Copy the output of the previous command, which should look something like:

   ```
   /Library/Java/JavaVirtualMachines/jdk-17.jdk/Contents/Home
   ```

4. Open the `.bash_profile` file in your home directory using a text editor. If the file doesn't exist, you can create it.

   ```
   nano ~/.bash_profile
   ```

5. Add the following line to the file, replacing `<paste Java path here>` with the path you copied in step 3:

   ```
   export JAVA_HOME=<paste Java path here>
   ```

6. Save the file and exit the text editor.

7. To apply the changes, you can either open a new Terminal window or run the following command:

   ```
   source ~/.bash_profile
   ```

8. Verify if the `JAVA_HOME` environment variable is set correctly by running:

   ```
   echo $JAVA_HOME
   ```

   It should output the path to your Java installation.

Once you have correctly set the `JAVA_HOME` environment variable, you should be able to use Maven without the error message.

## macOS打开隐藏目录：command+shift+G 

## GCC debug
#os

![[Pasted image 20230805013432.png]] 
![[Pasted image 20230805014143.png]]

![[Pasted image 20230805014856.png]]
怎么看.o文件？
	：readelf -h/s/ + 文件名

gcc  _-g_：带调试信息
![[Pasted image 20230805110752.png]]
![[Pasted image 20230805112837.png]]
