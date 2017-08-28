---
title: Time Code
---

<div class="tip">
    需要注意的是,本文中所有代码块为临时编写使用,无法在正式项目中使用.也无法编译通过！
</div>

``` java
package com.example.time;

public class CalcDay {

	public String calTime(int time) {
		int millisec = time % 100;
		int sec = (time % 6000) / 100;
		int min = time / 6000;
		if (min >= 60) {
			min %= 60;
		}
		String runningtime = null;
		String r_sec;
		String r_min;
		String r_milli;
		if (sec < 10) {
			r_sec = "0" + sec;
		} else {
			r_sec = sec + "";
		}
		if (min < 10) {
			r_min = "0" + min;
		} else {
			r_min = min + "";
		}
		if (millisec < 10) {
			r_milli = "0" + millisec;
		} else {
			r_milli = millisec + "";
		}
		runningtime = r_min + ":" + r_sec + "." + r_milli;
		return runningtime;
	}
}
```

``` java
package com.example.time;

import android.app.Activity;
import android.os.Bundle;
import android.os.Handler;
import android.os.Message;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends Activity implements OnClickListener {

	private Button btnStart, btnStop;
	private TextView tvTime;

	private boolean isStart;
	private int time = 0;

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);

		initView();
	}

	private void initView() {
		tvTime = (TextView) findViewById(R.id.tvTime);
		btnStart = (Button) findViewById(R.id.btn_open);
		btnStop = (Button) findViewById(R.id.btn_clean);
		btnStart.setOnClickListener(this);
		btnStop.setOnClickListener(this);
	}

	@Override
	public void onClick(View arg0) {
		switch (arg0.getId()) {
		case R.id.btn_open:
			StartOrStopTime();
			break;
		case R.id.btn_clean:
			calAndStop();
			break;
		default:
			break;
		}
	}

	private void StartOrStopTime() {
		if (!isStart) {
			new Thread(new MyThread()).start();
			isStart = true;
		} else {
			isStart = false;
		}
	}

	private void calAndStop() {
		isStart = false;
		time = 0;
		tvTime.setText(new CalcDay().calTime(time));
		Toast.makeText(MainActivity.this,
				time + " - " + new CalcDay().calTime(time), 0).show();
	}

	private static final int T_start = 1;

	public class MyThread implements Runnable {
		@Override
		public void run() {
			while (true) {
				if (!isStart) {
					break;
				}
				try {
					Thread.sleep(10);
					time += 1;
					Message message = new Message();
					message.what = T_start;
					handler.sendMessage(message);// 发送消息
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
			}
		}
	}

	Handler handler = new Handler() {
		@Override
		public void handleMessage(Message msg) {
			switch (msg.what) {
			case T_start:
				if (!isStart) {
					break;
				}
				tvTime.setText(new CalcDay().calTime(time));
				break;

			default:
				break;
			}
			super.handleMessage(msg);
		}
	};
}
```

``` xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity" >

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal" >

        <Button
            android:id="@+id/btn_open"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="Start&amp;Stop" />

        <Button
            android:id="@+id/btn_clean"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="Clean" />
    </LinearLayout>

    <TextView
        android:id="@+id/tvTime"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="10dp"
        android:gravity="center"
        android:text="00:00.00"
        android:textColor="#77000000"
        android:textSize="24sp" />

</LinearLayout>
```

http://blog.csdn.net/u013898922/article/details/43410285