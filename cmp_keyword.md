# 查找关键字
    void cmp1()//keyword
    {
        for(int i=0;i<txt.size();i++)
        {
            for(int j=0;j<33;j++)
            {
                if(key[j]==txt[i])
                {
                    total_num++;
                    if(txt[i]==key[15]||txt[i]==key[9])
                    if_else.push_back(txt[i]);//将if else关键字存入if_else
                    if(txt[i]==key[32])
                    {
                        if_else.push_back(txt[i]);
                        total_num++;
                    }
                    //cout<<txt[i]<<endl;
                }   
            }
        }
        cout<<"total num: "<<total_num<<endl;
    }
