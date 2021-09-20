# 主函数以及全局变量
    #include<bits/stdc++.h>
    using namespace std;
    vector<string> txt;
    map<int,string> key;
    vector<string> if_else;
    int total_num=0;
    int switch_num=0;
    int ifelse_num=0;
    int ifelse2_num=0;
    int main(void)
    {
        string fn;
        int lev;
        cin>>fn>>lev;//输入文件路径;
        file(fn.c_str());//对文件进行操作
        edit();//输入关键字
        if(lev==1)
        cmp1();
        if(lev==2)
        {
            cmp1();
            cmp2();
        }
        if(lev==3)
        {
            cmp1();
            cmp2();
            cmp3();
        }
        if(lev==4)
        {
            cmp1();
            cmp2();
            cmp3();
            cmp4();
        }
        system("pause");
        return 0;
    }
