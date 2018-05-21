# Hello
你好

import java.io.File;
import java.text.MessageFormat;
import java.util.Scanner;

public class Rename {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入你要修改文件的文件路径(请确保其中不含子文件夹)：");
        String path = sc.nextLine();

        //原始文件名遍历输出
        File f1 = new File(path);
        File[] files = f1.listFiles();
        for (File file : files) {
            System.out.println(file);
        }

        //设置文件名格式
        System.out.println("请输入你要修改的文件名及其格式：" +
                "如：新世界より{0}.ass  其中{0}代表文件序号的位置。" );
        String renameTo =sc.nextLine();//""
        //设置刚开始的集数
        System.out.println("请输入开始的序号：");
        int num = sc.nextInt();
        String numStr ="";
        for (int i = 0; i < files.length; i++) {
            int n = num + i;
            if (n < 10) {
                numStr = "" + 0 + n;
            } else {
                numStr ="" + n;
            }
            String value = MessageFormat.format(renameTo,numStr);
            new File(path,files[i].getName()).renameTo(new File(path,value));
        }
        //新文件名遍历输出
        File[] newFiles = f1.listFiles();
        for (File newFile : newFiles) {
            System.out.println(newFile);
        }

    }
}
