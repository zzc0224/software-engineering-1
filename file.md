    void file(const char* filename)//处理文件
    {
        ifstream infile(filename,ios::in);
        if(!infile) 
        {
            cout<<"open error!"<<endl; 
            exit(1);
        }
        vector<string> vec;
        vector<string> vec1;
        vector<string> vec2;
        vector<string> vec3;
        vector<string> word;
        string buf;
        while(getline(infile,buf))
        {
            vec.push_back(buf);
        }/*
        for(int i=0;i<vec.size();i++)
        {
            cout<<vec[i]<<endl;
        }*/
        for(int i=0;i<vec.size();i++)//去除//
        {
            string s=vec[i];
            for(int j=0;j<s.length();j++)
            {
                if(s[j]=='/'&&s[j+1]=='/')
                {
                    vec1.push_back(s.substr(0,j));
                    break;
                }
                if(j==s.length()-1)
                vec1.push_back(s);
            }
        }
        int b=0,e=0;
        for(int i=0;i<vec1.size();i++)//去除/**/
        {
            string s=vec1[i];
            for(int j=0;j<s.length();j++)
            {
                if(s[j]=='/'&&s[j+1]=='*')
                {
                    vec2.push_back(s.substr(0,j));
                b=i;
            }
            if(s[j]=='*'&&s[j+1]=='/')
            {
                vec2.push_back(s.substr(j+2,s.length()));
                e=i;
            }
            if((j==s.length()-1)&&b==0)
            vec2.push_back(s);
        }
        if(b<=e)
        {
            b=0;
            e=0;
        }
    }
    for(int i=0;i<vec2.size();i++)//去除”“
    {
        string s=vec2[i];
        for(int j=0;j<s.length();j++)
        {
            if(s[j]=='"')
            {
                if(b==0)
                {
                    vec3.push_back(s.substr(0,j));
                    b=i;
                    continue;
                }
                if(b!=0)
                {
                    vec3.push_back(s.substr(j+1,s.length()));
                    e=i;
                }
            }
            if((j==s.length()-1)&&b==0)
            vec3.push_back(s);
        }
        if(b==e)
        {
            b=0;
            e=0;
        }
    }
    
    for(int i=0;i<vec3.size();i++)
    {
        istringstream is(vec3[i]);
        string s;
        while(is>>s)
        {
            word.push_back(s);
        }
    }
    for(int i=0;i<word.size();i++)//elseif特别处理
    {
        if(word[i]=="else")
        {
            string s=word[i+1];
            if(s=="if")
            {
                word.erase(word.begin()+i);
                word.erase(word.begin()+i);
                word.insert(word.begin()+i,"elseif");
            }
            else
            {
                for(int j=0;j<s.length();j++)
                {
                    if(s[j]=='('&&s.substr(0,j)=="if")
                    {
                        word.erase(word.begin()+i);
                        word.erase(word.begin()+i);
                        word.insert(word.begin()+i,"elseif");
                    }
                }
            }
        }
    }
    for(int i=0;i<word.size();i++)//符号处理
    {
        string t=word[i];
        for(int j=0;j<t.length();j++)
        {
            if(t[j]=='(')
            {
                txt.push_back(t.substr(0,j));
                break;
            }
            if(t[j]=='{')
            {
                txt.push_back(t.substr(0,j));
                break;
            }
            if(t[j]==';')
            {
                txt.push_back(t.substr(0,j));
                break;
            }
            if(t[j]==':')
            {
                txt.push_back(t.substr(0,j));
                break;
            }
            if(j==t.length()-1)
            txt.push_back(t);
        }
    }
    /*for(int i=0;i<txt.size();i++)
    cout<<txt[i]<<endl;*///测试输出
    infile.close();
}
