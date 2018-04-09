# Helloworld
Hello World
package unicode;

import java.io.UnsupportedEncodingException;

public class Utf8Demo06 {

	public static void main(String[] args) {
		/**
		 * 将一个字符编码转换为UTF-8
		 */
		String a=utf('你');
		String b=utf('好');
		String c=utf('阿');
		System.out.println(a+b+c);
		int e=20000;
		System.out.println((char)(e));
	}
	public static String utf(char a)  {
		int c=a;
		int b3=c & 0x3f | 0x80;	   //第一组
		int b2=c>>>6 & 0x3f | 0x80;//第二组
		int b1=c>>>12 & 0xf | 0xe0;//第三组
		byte[] bytes={(byte)b1,(byte)b2,(byte)b3};
		String s="";
		System.out.println(bytes[0]);
		try {
			s=new String(bytes, "UTF-8");
		} catch (UnsupportedEncodingException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
			throw  new RuntimeException();
		}
		int ch=(b1&0xf)<<12|(b2&0x3f)<<6|(b3&0x3f);
		System.out.println(ch+".");
		System.out.println();
		System.out.println((char)(ch));
		return s;
	}
}
