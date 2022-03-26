package com.mahekarim.calculator;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.text.SpannableStringBuilder;
import android.view.View;
import android.widget.EditText;
import org.mariuszgromada.math.mxparser.*;

public class MainActivity extends AppCompatActivity {

    private EditText display;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        display = findViewById(R.id.textView);
        display.setShowSoftInputOnFocus(false);
        display.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                if (getString(R.string.display).equals(display.getText().toString())) {
                    display.setText("");
                }
            }
        });
    }

    private void updateText(String strToAdd) {
        String oldStr = display.getText().toString();
        int cursorPosition = display.getSelectionStart();
        String leftStr = oldStr.substring(0, cursorPosition);
        String rightStr = oldStr.substring(cursorPosition);

        if (getString(R.string.display).equals(display.getText().toString()))
        {
            display.setText(strToAdd);
            display.setSelection(cursorPosition + 1);

        } else {
            display.setText(String.format("%s%s%s", leftStr, strToAdd, rightStr));
            // Cursor Position
            display.setSelection(cursorPosition + 1);
        }

    }


    public void zeroBtn(View view) {
        updateText("0");
    }
    public void oneBtn(View view) {
        updateText("1");
    }
    public void twoBtn(View view) {
        updateText("2");
    }
    public void threeBtn(View view) {
        updateText("3");
    }
    public void fourBtn(View view) {
        updateText("4");
    }
    public void fiveBtn(View view) {
        updateText("5");
    }
    public void sixBtn(View view) {
        updateText("6");
    }
    public void sevenBtn(View view) {
        updateText("7");
    }
    public void eightBtn(View view) {
        updateText("8");
    }
    public void nineBtn(View view) {
        updateText("9");
    }
    public void plusBtn(View view) {
        updateText("+");
    }
    public void minusBtn(View view) {
        updateText("-");
    }
    public void multiplyBtn(View view) {
        updateText("*");
    }
    public void dividedBtn(View view) {
        updateText("/");
    }
    public void pointBtn(View view) {
        updateText(".");
    }
    public void clearBtn(View view) {
        display.setText("");
    }
    public void parenthesesBtn(View view) {
        int cursorPos = display.getSelectionStart();
        int openPar = 0 ;
        int closePar = 0 ;

        int textLen = display.getText().length();
        for (int i = 0; i < cursorPos; i++ ) {
            if(display.getText().toString().substring(i, i+1).equals("(")) {
                openPar += 1 ;
            }
            if(display.getText().toString().substring(i, i+1).equals(")")) {
                closePar += 1 ;
            }
        }
        if (openPar == closePar || display.getText().toString().substring(textLen-1, textLen).equals("(")) {
            updateText("(");
        } else if (closePar < openPar && display.getText().toString().substring(textLen-1, textLen).equals("(")) {
            updateText(")");
        }
        display.setSelection(cursorPos + 1);

    }
    public void expBtn(View view) {

    }
    public void backspaceBtn(View view) {
        int cursorPos = display.getSelectionStart();
        int textLen = display.getText().length();

        if (cursorPos != 0 && textLen != 0 ) {
            SpannableStringBuilder selection = (SpannableStringBuilder) display.getText();
            selection.replace(cursorPos - 1, cursorPos, "");
            display.setText(selection);
            display.setSelection(cursorPos - 1);
        }
    }

    public void plusMinusBtn(View view) {
        updateText("-");
    }

    public void equalsBtn(View view) {
        String userExp = display.getText().toString();
        userExp = userExp.replaceAll("/", "/");
//      userExp = userExp.replaceAll("*", "*");

        Expression exp = new Expression(userExp);
        String result = String.valueOf(exp.calculate());

        display.setText(result);
        display.setSelection(result.length());
    }
}