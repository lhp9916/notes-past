# 循环任务

```java
Handler handler = new Handler();
int i = 1;

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    Runnable runnable = new Runnable() {
        @Override
        public void run() {
            Log.d("lhp", "run: " + i);
            handler.postDelayed(this, 3000);//3秒延时时长
            i++;
        }
    };
    handler.postDelayed(runnable, 3000);// 打开定时器，执行操作
}

@Override
protected void onDestroy() {
    //移除定时器
    handler.removeCallbacks(runnable);
    super.onDestroy();
}
```