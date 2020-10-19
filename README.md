#include <bits/stdc++.h>
#include <iostream>
#include <fstream>
#include <vector>
using namespace std;
const int N=1e6;
int flaga=0;
vector<vector<int> >g(N);
vector<bool> visited(N);
vector<int>path(N);
char tab[10000][10000];
void bfs(int s,int koniec)
{
    queue<int>q;
    q.push(s);
    visited[s]=true;
    while(!q.empty())
        {
            int cur=q.front();
            q.pop();
           // cout<<"I'm in: "<<cur<<endl;
            if(cur==koniec) flaga=1;
           // cout<<g[cur].size()<<endl;
            for(int i=0;i<g[cur].size();i++)
            {
               if(!visited[g[cur][i]])
                {
                //   cout<<"current: "<<g[cur][i]<<endl;
                    path[g[cur][i]]=cur;
                    q.push(g[cur][i]);
                    visited[g[cur][i]]=true;
                }
            }
        }
}
int main()
{
    ios_base::sync_with_stdio(0);

int s,d,licz=0,start,koniec,ILE;

char k;
cin>>ILE;
for(int kk=0;kk<ILE;kk++)
{
    flaga=0;

cin>>s>>d;
 for(int i=0;i<licz+1;i++)
    {
        visited[i]=0;
    path[i]=0;
    g[i].clear();

    }
    licz=0;
for(int i=0;i<s;i++)
{
    for(int j=0;j<d;j++)
    {
        cin>>k;
        tab[i][j]=k;
    }
}
if(s==1&&d==1&&tab[0][0]=='>')cout<<"NO PATH"<<endl;
else{
        if(s==2)
        {

            for(int i=0;i<s;i++)
            {

    if(i==0)
    {
   for(int j=0;j<d;j++)
   {
       if(tab[i][j]!='#')
       {
           if(tab[i][j]=='>')
           {
               koniec=licz;
           }
           if(tab[i][j]=='@')
           {
               start=licz;
           }
       int dod=licz+1;
       int odej=licz-1;
       if(i==0&&j==0)
       {
           if(tab[0][j+1]!='#')
           {
           g[licz].push_back(dod);

           }
           if(tab[1][j]!='#')g[licz].push_back(licz+d);

       }
       else if(i==0&&j==d-1)
       {
           if(tab[0][j-1]!='#')
           {
        g[licz].push_back(odej);
           }
           if(tab[1][j]!='#')g[licz].push_back(licz+d);

       }
       else{
            if(tab[0][j+1]!='#')
              {
                g[licz].push_back(dod);
               

              }
        if(tab[0][j-1]!='#')
        {
            g[licz].push_back(odej);
           

        }
        if(tab[1][j]!='#')g[licz].push_back(licz+d);
       }
   }
   licz++;
   }
 }
else
    {
        for(int j=0;j<d;j++)
        {
            if(tab[i][j]!='#')
            {
                  if(tab[i][j]=='>')
           {
               koniec=licz;
           }
             if(tab[i][j]=='@')
           {
               start=licz;
           }
            int dod=licz+1;
       int odej=licz-1;
        if(i==s-1&&j==0)
        {
            if(tab[s-1][j+1]!='#')
            {
            g[licz].push_back(dod);

            }
            if(tab[s-2][j]!='#')
            {
                g[licz].push_back(licz-d);
            }
        }

       else  if(i==s-1&&j==d-1)
        {
            if(tab[s-1][j-1]!='#')
            {
            g[licz].push_back(odej);
        }
        if(tab[s-2][j]!='#')g[licz].push_back(licz-d);

        }
        else
        {
       if(tab[s-1][j+1]!='#')
{
g[licz].push_back(dod);


}
        if(tab[s-1][j-1]!='#')//tyl
        {

            g[licz].push_back(odej);
      

        }
        if(tab[s-2][j]!='#')g[licz].push_back(licz-d);
        }
            }
        licz++;
        }
    }
            }
            int obec=koniec,cou=0;

bfs(start,koniec);
path[start]=-1;
if(flaga==0)
{
    cout<<"NIE"<<endl;
}
else
{
while(obec!=-1)
    {

    obec=path[obec];
    cou++;
    }

    cout<<cou-1<<endl;
}

        }
        else
        {
for(int i=0;i<s;i++)
{

    if(i==0)
    {
   for(int j=0;j<d;j++)
   {
       if(tab[i][j]!='#')
       {
           if(tab[i][j]=='>')
           {
               koniec=licz;
           }
           if(tab[i][j]=='@')
           {
               start=licz;
           }
       int dod=licz+1;
       int odej=licz-1;
       if(i==0&&j==0)
       {
           if(tab[0][j+1]!='#')
           {
           g[licz].push_back(dod);
           }

       }
       else if(i==0&&j==d-1)
       {
           if(tab[0][j-1]!='#')
           {
        g[licz].push_back(odej);

           }

       }
       else{
            if(tab[0][j+1]!='#')
              {
                g[licz].push_back(dod);
        

              }
        if(tab[0][j-1]!='#')
        {
            g[licz].push_back(odej);

        }
       }
   }
   licz++;
   }
   }//
   else if(i==s-1)
    {
        for(int j=0;j<d;j++)
        {
            if(tab[i][j]!='#')
            {
                  if(tab[i][j]=='>')
           {
               koniec=licz;
           }
             if(tab[i][j]=='@')
           {
               start=licz;
           }
            int dod=licz+1;
       int odej=licz-1;
        if(i==s-1&&j==0)
        {
            if(tab[s-1][j+1]!='#')
            {
            g[licz].push_back(dod);
            }
        }

       else  if(i==s-1&&j==d-1)
        {
            if(tab[s-1][j-1]!='#')
            {
            g[licz].push_back(odej);

        }

        }
        else
        {
       if(tab[s-1][j+1]!='#')
{
g[licz].push_back(dod);

}
        if(tab[s-1][j-1]!='#')//tyl
        {

            g[licz].push_back(odej);
        }
        }
            }
        licz++;
        }
    }

    else{
        for(int j=0;j<d;j++)
        {

if(tab[i][j]!='#')
                {
                     if(tab[i][j]=='>')
           {
               koniec=licz;
           }
             if(tab[i][j]=='@')
           {
               start=licz;
           }
            if(j==0&& i!=0&&i!=s-1)
            {
                if(tab[i-1][0]!='#')
                {
                g[licz].push_back(licz-d);
                 g[licz-d].push_back(licz);

                }
                if(tab[i+1][0]!='#')//dol
                {
                 g[licz].push_back(licz+d);

                  g[licz+d].push_back(licz);

                }
                   if(tab[i][1]!='#')//prawo
                   {
                   g[licz].push_back(licz+1);
                   }

            }

          else  if(j==d-1&&i!=0&&i!=s-1) 
            {
                if(tab[i-1][j]!='#')
                {
                 g[licz].push_back(licz-d);
                 g[licz-d].push_back(licz);
                }
                 if(tab[i+1][j]!='#')
                 {
                 g[licz].push_back(licz+d);
                 g[licz+d].push_back(licz);

                 }
                 if(tab[i][j-1]!='#')
                 {


                 g[licz].push_back(licz-1);

                 }

            }
            else
            {
                if(tab[i-1][j]!='#')
                {
                 g[licz].push_back(licz-d);
                 g[licz-d].push_back(licz);

                }
                if(tab[i+1][j]!='#')
                {
                 g[licz].push_back(licz+d);
                 g[licz+d].push_back(licz);

                }
                if(tab[i][j+1]!='#')
                {
                 g[licz].push_back(licz+1);
           

                }
                if(tab[i][j-1]!='#')
                {
                 g[licz].push_back(licz-1);
               

                }
            }

        }
        licz++;
            }
        }
    }

int obec=koniec,cou=0;

bfs(start,koniec);
path[start]=-1;
if(flaga==0)
{
    cout<<"NIE"<<endl;
}
else
{
while(obec!=-1)
    {

    obec=path[obec];
    cou++;
    }

    cout<<cou-1<<endl;
}
        }
}
}
}


