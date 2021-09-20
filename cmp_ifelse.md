# 查找if=else , if-elseif-else
    void cmp3()//if-else if-elseif-else
    {
        stack<string> sta;
        for(int i=0;i<if_else.size();i++)
        {
            if(if_else[i]=="if")
            {
                sta.push("if");
            }
            if(if_else[i]=="elseif")
            {
                sta.push("elseif");
            }
            if(if_else[i]=="else")
            {
                if(sta.top()=="if")
                {
                    ifelse_num++;
                }
                if(sta.top()=="elseif")
                {
                    ifelse2_num++;
                    while(!sta.empty() && sta.top().compare("elseif"))
                    {
                        sta.pop();
                    }
                    sta.pop();//弹出if
                }
            }

        }
        cout<<"if-else num: "<<ifelse_num<<endl;
    }
    void cmp4()
    {
        cout<<"if-elseif-else num: "<<ifelse2_num<<endl;
    }
