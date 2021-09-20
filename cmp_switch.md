# 统计switch case
    void cmp2()//switch case
    {
        int case_num[txt.size()]={0};
        for(int i=0;i<txt.size();i++)
        {
            if(txt[i]==key[25])
            {
                switch_num++;
                for(int j=i+1;j<txt.size();j++)
                {
                    if(txt[j]==key[2])
                    case_num[switch_num-1]++;
                    if(txt[j]==key[25])
                    {
                        i=j-1;
                        break;
                    }
                }
            }
        }
        cout<<"switch_num: "<<switch_num<<endl;
        cout<<"case_num: ";
        for(int i=0;i<switch_num;i++)
        cout<<case_num[i]<<" ";
        cout<<endl;
    }
