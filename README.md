# Mobile_Program
## 안드로이드앱구조

---------------
XML을 사용하여 작성
---------------
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
<?xml version="1.0" encoding="utf-8" ?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="이름: 홍길동\n프로그래밍 능력: Java(중), Python(상)\n국적: 대한민국\n연락처: gdhong@example.com"/>
</LinearLayout>


------------------
XML을 사용하지 않고 작성
------------------
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        LinearLayout ll=new LinearLayout(this);
        TextView tv=new TextView(this);
        tv.setText("이름: 홍길동\n프로그래밍 능력: Java(중), Python(상)\n국적: 대한민국\n연락처: gdhong@example.com");
        ll.addView(tv);
        setContentView(ll);
    }
}


## 이벤트처리




-----
### 실습 1
-----

---------------- activity_main.xml ----------------
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="20dp"
    android:gravity="center_horizontal"
    android:orientation="vertical">
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="문제 1: 대한민국의 수도는?"
        android:textSize="20sp"/>
    <TextView
        android:id="@+id/textview"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="20sp"/>
</LinearLayout>
---------------- activity_main.xml ----------------

---------------- MainActivity.java ----------------
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button button=findViewById(R.id.button);
        TextView textview=findViewById(R.id.textview);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                textview.setText("정답: 서울");
            }
        });
    }
}
---------------- MainActivity.java ----------------




-----
### 실습 2
-----

---------------- activity_main.xml ----------------
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="20dp"
    android:gravity="center_horizontal"
    android:orientation="vertical">
    <EditText
        android:id="@+id/edittext"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:hint="텍스트를 입력하세요"
        android:textSize="20sp"/>
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="텍스트 길이 계산"
        android:textSize="20sp"/>
    <TextView
        android:id="@+id/textview"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="20sp"/>
</LinearLayout>
---------------- activity_main.xml ----------------

---------------- MainActivity.java ----------------
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button button=findViewById(R.id.button);
        EditText edittext=findViewById(R.id.edittext);
        TextView textview=findViewById(R.id.textview);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String s=edittext.getText().toString();
                textview.setText(""+s.length());
            }
        });
    }
}
---------------- MainActivity.java ----------------




-----
### 실습 3
-----

---------------- activity_main.xml ----------------
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="20dp"
    android:gravity="center_horizontal"
    android:orientation="vertical">
    <EditText
        android:id="@+id/edittext"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:hint="화씨온도를 입력하세요"
        android:textSize="20sp"/>
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="섭씨 온도"
        android:textSize="20sp"/>
    <TextView
        android:id="@+id/textview"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="20sp"/>
</LinearLayout>
---------------- activity_main.xml ----------------

---------------- MainActivity.java ----------------
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button button=findViewById(R.id.button);
        EditText edittext=findViewById(R.id.edittext);
        TextView textview=findViewById(R.id.textview);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String s=edittext.getText().toString();
                s.length();
                double f=Double.parseDouble(s);
                double c=(f-32.)*5./9.;
                String d=String.format("%.2f", c);
                textview.setText("섭씨 "+d+" (도)");
            }
        });
    }
}
---------------- MainActivity.java ----------------











## 사용자인터페이스기초


-----
### 실습 1
-----
public class MainActivity extends AppCompatActivity {
    LinkedList<String> carType=new LinkedList<>();
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        RadioButton radiobutton_gasoline=findViewById(R.id.radiobutton_gasoline);
        RadioButton radiobutton_diesel=findViewById(R.id.radiobutton_diesel);
        RadioButton radiobutton_electric=findViewById(R.id.radiobutton_electric);
        RadioButton radiobutton_etc=findViewById(R.id.radiobutton_etc);
        Button button_submit=findViewById(R.id.button_submit);
        button_submit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String s="";
                if(radiobutton_gasoline.isChecked()) s=radiobutton_gasoline.getText().toString();
                if(radiobutton_diesel.isChecked()) s=radiobutton_diesel.getText().toString();
                if(radiobutton_electric.isChecked()) s=radiobutton_electric.getText().toString();
                if(radiobutton_etc.isChecked()) s=radiobutton_etc.getText().toString();
                Toast.makeText(getApplicationContext(), "차량 유형: "+s, Toast.LENGTH_SHORT).show();
            }
        });
    }
}
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_margin="20dp"
    android:orientation="vertical">
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:padding="20dp"
        android:textSize="20sp"
        android:text="차량 유형 선택" />
    <RadioGroup
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical">
        <RadioButton
            android:id="@+id/radiobutton_gasoline"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="휘발유" />
        <RadioButton
            android:id="@+id/radiobutton_diesel"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="경유" />
        <RadioButton
            android:id="@+id/radiobutton_electric"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="전기" />
        <RadioButton
            android:id="@+id/radiobutton_etc"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="기타" />
    </RadioGroup>
    <Button
        android:id="@+id/button_submit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:text="제출"/>

</LinearLayout>



-----
### 실습 2
-----
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        CheckBox checkbox_seoul=findViewById(R.id.checkbox_seoul);
        CheckBox checkbox_jeju=findViewById(R.id.checkbox_jeju);
        CheckBox checkbox_etc=findViewById(R.id.checkbox_etc);
        Button button_submit=findViewById(R.id.button_submit);
        button_submit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String s="<방문 지역>";
                if(checkbox_seoul.isChecked()) s+="\n"+checkbox_seoul.getText();
                if(checkbox_jeju.isChecked()) s+="\n"+checkbox_jeju.getText();
                if(checkbox_etc.isChecked()) s+="\n"+checkbox_etc.getText();
                Toast.makeText(getApplicationContext(), s, Toast.LENGTH_SHORT).show();
            }
        });
    }
}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_margin="20dp"
    android:orientation="vertical">
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:padding="20dp"
        android:textSize="20sp"
        android:text="방문 지역 모두 선택 (최근 1년)" />
    <CheckBox
        android:id="@+id/checkbox_seoul"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="left"
        android:padding="20dp"
        android:text="서울" />
    <CheckBox
        android:id="@+id/checkbox_jeju"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="left"
        android:padding="20dp"
        android:text="제주도" />
    <CheckBox
        android:id="@+id/checkbox_etc"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="left"
        android:padding="20dp"
        android:text="그 외 지역" />
    <Button
        android:id="@+id/button_submit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:text="제출" />
</LinearLayout>



-----
### 실습 3
-----
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        EditText edittext_width=findViewById(R.id.edittext_width);
        EditText edittext_height=findViewById(R.id.edittext_height);
        RadioButton radiobutton_white=findViewById(R.id.radiobutton_white);
        RadioButton radiobutton_brown=findViewById(R.id.radiobutton_brown);
        RadioButton radiobutton_black=findViewById(R.id.radiobutton_black);
        radiobutton_white.setChecked(true);
        CheckBox checkbox_tool=findViewById(R.id.checkbox_tool);
        TextView textview_display=findViewById(R.id.textview_display);
        Button button_display=findViewById(R.id.button_display);
        button_display.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                LinkedList<String> list=new LinkedList<>();
                list.add("가로:"+edittext_width.getText()+"(mm)");
                list.add("세로:"+edittext_height.getText()+"(mm)");
                list.add("색상:"+(radiobutton_white.isChecked()? "화이트" : radiobutton_brown.isChecked()? "브라운" : "블랙"));
                list.add("추가공구: "+(checkbox_tool.isChecked()? "필요" : "불필요"));
                textview_display.setText("<주문내역>\n"+list);
            }
        });
    }
}
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_margin="20dp"
    android:gravity="center_horizontal"
    android:orientation="vertical">
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:padding="20dp"
        android:textSize="20sp"
        android:text="주문 내역 작성" />
    <EditText
        android:id="@+id/edittext_width"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:hint="가로 길이 (mm)"/>
    <EditText
        android:id="@+id/edittext_height"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:hint="세로 길이 (mm)"/>
    <RadioGroup
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:orientation="horizontal">
        <RadioButton
            android:id="@+id/radiobutton_white"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="화이트" />
        <RadioButton
            android:id="@+id/radiobutton_brown"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="브라운" />
        <RadioButton
            android:id="@+id/radiobutton_black"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="블랙" />
    </RadioGroup>
    <CheckBox
        android:id="@+id/checkbox_tool"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="설치 공구 필요 (+2000)"/>
    <Button
        android:id="@+id/button_display"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="주문 내역 확인"/>
    <TextView
        android:id="@+id/textview_display"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="15sp"/>
</LinearLayout>



-----
### 실습 4
-----
public class MainActivity extends AppCompatActivity {
    private String regison[]={"(거주지) 서울", "(거주지) 부산", "(거주지) 기타"};
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        TextView textview_display=findViewById(R.id.textview_display);
        Spinner spinner_region=findViewById(R.id.spinner_region);
        Button button_submit=findViewById(R.id.button_submit);
        EditText edittext_name=findViewById(R.id.edittext_name);
        RadioButton radiobutton_korean=findViewById(R.id.radiobutton_korean);
        RadioButton radiobutton_foreigner=findViewById(R.id.radiobutton_foreigner);
        radiobutton_korean.setChecked(true);
        CheckBox checkbox_walk=findViewById(R.id.checkbox_walk);
        CheckBox checkbox_sleep=findViewById(R.id.checkbox_sleep);

        ArrayAdapter adapter=new ArrayAdapter(this, android.R.layout.simple_spinner_item, regison);
        adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item);
        spinner_region.setAdapter(adapter);
        button_submit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if(edittext_name.getText().length()==0) { msg("이름을 입력하세요"); return; }
                if(!radiobutton_korean.isChecked() && !radiobutton_foreigner.isChecked()) { msg("한국인, 외국인 선택하세요"); return; }
                String s="이름: "+edittext_name.getText()+", "+spinner_region.getSelectedItem();
                if(radiobutton_korean.isChecked()) s+=", "+radiobutton_korean.getText();
                if(radiobutton_foreigner.isChecked()) s+=", "+radiobutton_foreigner.getText();
                if(checkbox_walk.isChecked()) s+=", "+checkbox_walk.getText();
                if(checkbox_sleep.isChecked()) s+=", "+checkbox_sleep.getText();
                textview_display.setText(s);
            }
        });
    }
    private void msg(String v) {
        Toast.makeText(getApplicationContext(), v, Toast.LENGTH_SHORT).show();
    }
}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_margin="80dp"
    android:gravity="center_horizontal"
    android:orientation="vertical">
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:padding="20dp"
        android:textSize="20sp"
        android:text="진료 신청" />
    <EditText
        android:id="@+id/edittext_name"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:hint="이름"/>
    <Spinner
        android:id="@+id/spinner_region"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="left"
        style="@style/Widget.AppCompat.Spinner.Underlined"/>
    <RadioGroup
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">
        <RadioButton
            android:id="@+id/radiobutton_korean"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="한국인" />
        <RadioButton
            android:id="@+id/radiobutton_foreigner"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="외국인" />
    </RadioGroup>
    <CheckBox
        android:id="@+id/checkbox_walk"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="하루 30이상 걷습니다"/>
    <CheckBox
        android:id="@+id/checkbox_sleep"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="하루 6시간 이상 수면을 취합니다"/>
    <Button
        android:id="@+id/button_submit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"

        android:text="진료 신청"/>
    <TextView
        android:id="@+id/textview_display"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="15sp"/>
</LinearLayout>



-----
### 실습 5
-----
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        EditText edittext_id=findViewById(R.id.edittext_id);
        EditText edittext_password=findViewById(R.id.edittext_password);
        Button button_login=findViewById(R.id.button_login);
        button_login.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String msg="아이디:"+edittext_id.getText()+", 패스워드:"+edittext_password.getText();
                Toast.makeText(getApplicationContext(), msg, Toast.LENGTH_SHORT).show();
            }
        });
    }
}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="50dp"
    android:orientation="vertical">
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">
        <TextView
            android:layout_width="0dp"
            android:layout_weight="1"
            android:layout_height="wrap_content"
            android:padding="10dp"
            android:gravity="right"
            android:textSize="20sp"
            android:text="아이디" />
        <EditText
            android:id="@+id/edittext_id"
            android:layout_width="0dp"
            android:layout_weight="2"
            android:layout_height="wrap_content"
            android:padding="10dp"
            android:layout_gravity="left"
            android:textSize="20sp"/>
    </LinearLayout>
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">
        <TextView
            android:layout_width="0dp"
            android:layout_weight="1"
            android:layout_height="wrap_content"
            android:padding="10dp"
            android:gravity="right"
            android:textSize="20sp"
            android:text="패스워드" />
        <EditText
            android:id="@+id/edittext_password"
            android:layout_width="0dp"
            android:layout_weight="2"
            android:layout_height="wrap_content"
            android:padding="10dp"
            android:layout_gravity="left"
            android:inputType="textPassword"
            android:textSize="20sp"/>
    </LinearLayout>
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>
    <Button
        android:id="@+id/button_login"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="right"
        android:text="로그인"
        android:textSize="20sp"/>
</LinearLayout>



-----
### 실습 6
-----
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android&quot;
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:textSize="40sp"
        android:text="북" />
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1"
        android:orientation="horizontal">
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center"
            android:textSize="40sp"
            android:text="서" />
        <TextView
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="1" />
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:gravity="center"
            android:textSize="40sp"
            android:text="동" />
    </LinearLayout>
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:textSize="40sp"
        android:text="남" />
</LinearLayout>

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
