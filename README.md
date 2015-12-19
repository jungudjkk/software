# software
茅山光大大小组软件开发工作室
package com.example.XXSCYS;
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.FileOutputStream;

import android.os.Bundle;
import android.app.Activity;
import android.app.AlertDialog;
import android.app.AlertDialog.Builder;
import android.content.Context;
import android.content.Intent;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends Activity {
	public static final String FILENAME = "setting.set";
	public static final String FILENAME1 = "mima.set";
	public static final String FILENAME0 = "zancun.set"; 
	private EditText et; 
	private EditText et1;
	private EditText et2;
	TextView text;
	String c;
	OnClickListener listener1 = null;//监听器初始化
	OnClickListener listener2 = null;
	OnClickListener listener3 = null;
	OnClickListener listener4 = null;
	String a;
	String b;
	Button button1;//定义按钮
	TextView textView;
	TextView textView1;
	CheckBox CheckBox;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        text=(TextView) findViewById(R.id.editText3);
		b=readFiles0();	
		text.setText(b);
		//登录
		listener1 = new OnClickListener() {
			public void onClick(View v) {
				et=(EditText)findViewById(R.id.editText2);
				et1=(EditText)findViewById(R.id.editText3);
				c=readFiles1();
				a=readFiles();
				if(et.getText().toString().equals(c) && et1.getText().toString().equals(a)){
					 /*AlertDialog.Builder builder  = new Builder(MainActivity.this);
					 builder.setTitle("信息提醒" ) ;
					 builder.setMessage("密码输入正确！！" ) ;
					 builder.setPositiveButton("确定" ,  null );
					 */
					 et.setText("");
	                 Intent intent = new Intent(MainActivity.this, onectivity.class);
	    		     startActivity(intent);
	    		     //builder.show(); 
				      }
				else{
					 AlertDialog.Builder builder  = new Builder(MainActivity.this);
					 builder.setTitle("信息提醒" ) ;
					 builder.setMessage("密码错误！请重新输入！") ;
					 builder.setPositiveButton("确定" ,  null );
					 builder.show(); 
					 et.setText("");
					
				}
				
			}
		};
		
		//注册
		listener2 = new OnClickListener() {
			public void onClick(View v) {
				setTitle("注册");
                Intent intent1 = new Intent(MainActivity.this, zhuce.class);
				startActivity(intent1);
			}
		};
		
		//忘记密码
		listener3 = new OnClickListener() {
			public void onClick(View v) {
				 a=readFiles();
				 AlertDialog.Builder builder  = new Builder(MainActivity.this);
				 builder.setTitle("信息提醒" ) ;
				 builder.setMessage("请联系客服光大大设计者拿回密码！") ;
				 builder.setPositiveButton("确定" ,  null );
				 builder.show(); 
				 //et.setText("");
			}
		};
		
		//记住我
		listener4 = new OnClickListener() {
			public void onClick(View v) {
				et2=(EditText)findViewById(R.id.editText3);
				writeFiles0(et2.getText().toString());
			}
		};
		setContentView(R.layout.activity_main);
		button1 = (Button) findViewById(R.id.denglu);
		button1.setOnClickListener(listener1);
	
		textView = (TextView) findViewById(R.id.zhuce);
		textView.setOnClickListener(listener2);
		
		textView1 = (TextView) findViewById(R.id.wangji);
		textView1.setOnClickListener(listener3);
		
		CheckBox = (CheckBox) findViewById(R.id.jizhu);
		CheckBox.setOnClickListener(listener4);
		
		
	}
    
    // 保存文件暂时保存账号内容  
    private void writeFiles0(String content) {  
        try {  
            // 打开文件获取输出流，文件不存在则自动创建  
            FileOutputStream fos0 = openFileOutput(FILENAME0,  
                    Context.MODE_PRIVATE);  
            fos0.write(content.getBytes());  
            fos0.close();  
        } catch (Exception e) {  
            e.printStackTrace();  
        }  
    }  
    
    
    
    // 读取文件内容  
    private String readFiles0() {  
        String content = null ;  
        try {  
            FileInputStream fis = openFileInput(FILENAME0);  
            ByteArrayOutputStream baos = new ByteArrayOutputStream();  
            byte[] buffer = new byte[1024];  
            int len = 0;  
            while ((len = fis.read(buffer)) != -1) {  
                baos.write(buffer, 0, len);  
            }  
            content = baos.toString();  
            fis.close();  
            baos.close();  
        } catch (Exception e) {  
            e.printStackTrace();  
        }  
        return content;  
    }  
    
    
    // 读取文件内容  
    private String readFiles() {  
        String content = null ;  
        try {  
            FileInputStream fis = openFileInput(FILENAME);  
            ByteArrayOutputStream baos = new ByteArrayOutputStream();  
            byte[] buffer = new byte[1024];  
            int len = 0;  
            while ((len = fis.read(buffer)) != -1) {  
                baos.write(buffer, 0, len);  
            }  
            content = baos.toString();  
            fis.close();  
            baos.close();  
        } catch (Exception e) {  
            e.printStackTrace();  
        }  
        return content;  
    }  
    
 // 读取文件内容  
    private String readFiles1() {  
        String content1 = null ;  
        try {  
            FileInputStream fis = openFileInput(FILENAME1);  
            ByteArrayOutputStream baos = new ByteArrayOutputStream();  
            byte[] buffer = new byte[1024];  
            int len = 0;  
            while ((len = fis.read(buffer)) != -1) {  
                baos.write(buffer, 0, len);  
            }  
            content1 = baos.toString();  
            fis.close();  
            baos.close();  
        } catch (Exception e) {  
            e.printStackTrace();  
        }  
        return content1;  
    }  
}
