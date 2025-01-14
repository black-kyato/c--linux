1. 词频统计的作业再用map/unordered_map容器去实现一次，体验一下使用vector/map/unordered_map时程序执行的速度 

2. 文本查询作业
该程序将读取用户指定的任意文本文件【当前目录下的china_daily.txt】，
然后允许用户从该文件中查找单词。查询的结果是该单词出现的次数，并列
出每次出现所在的行。如果某单词在同一行中多次出现，程序将只显示该行
一次。行号按升序显示。

要求：
a. 它必须允许用户指明要处理的文件名字。

b. 程序将存储该文件的内容，以便输出每个单词所在的原始行。
vector<string> lines;//O(1)  完美hash
或 map<int, string> lines;//O(logN)
或 unorderedmap<int,string> lines;//O(1) 

c. 它必须将每一行分解为各个单词，并记录每个单词所在的所有行。 
在输出行号时，应保证以升序输出，并且不重复。 

map<string, set<int> > word2Line;
map<string, int> dict;

d. 对特定单词的查询将返回出现该单词的所有行的行号。

e. 输出某单词所在的行文本时，程序必须能根据给定的行号从输入
文件中获取相应的行。

示例：
使用提供的文件内容，然后查找单词 "element"。输出的前几行为：
---------------------------------------------
element occurs 125 times.
(line 62) element with a given key.
(line 64) second element with the same key.
(line 153) element |==| operator.
(line 250) the element type.
(line 398) corresponding element.
---------------------------------------------   

程序接口[可选]:
class TextQuery
{
public:
    void readFile(const string filename);
    void query(const string & word);
private:
    //......

};

//程序测试用例
int main(int argc, char *argv[])
{
    string  queryWord("hello");

    TextQuery tq;
    tq.readFile("test.dat");
    tq.query(queryWord);            
    return 0;

}                                           

3. Leetcode 146 LRU 
O(1)时间复杂度实现一个LRU cache 调页算法
4. 实现一个堆排序算法

可选择使用模板或非模板的实现：
