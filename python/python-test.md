
# Table of Contents

1.  [リスト](#org61189dc)
    1.  [リストの作成と要素へのアクセス方法](#orgf35666a)
    2.  [すべての部分集合の生成](#orge0a04a1)

\#+author masayuki


<a id="org61189dc"></a>

# リスト


<a id="orgf35666a"></a>

## リストの作成と要素へのアクセス方法

    ary = [0,1,2,3,4,5,6];
    print (ary) # 変数 ary の中身の値はリスト
    print (ary[0]) # 0番目の要素
    print (ary[-1])  # 最後の要素
    print (ary[1:])  # 1番目から残りすべての要素のリスト
    print (ary+[4])
    print (range(0,len(ary))) # 範囲を表す値 (rangeオブジェクト)
    
    # 繰り返し文
    
    for i in range(1,len(ary)-1):
        print(ary[i])

    [0, 1, 2, 3, 4, 5, 6]
    0
    6
    [1, 2, 3, 4, 5, 6]
    [0, 1, 2, 3, 4, 5, 6, 4]
    range(0, 7)
    1
    2
    3
    4
    5


<a id="orge0a04a1"></a>

## すべての部分集合の生成

-   集合をリストで表す
    
    集合とリストの処理  
    
    -   s<sub>all</sub> = [s<sub>1</sub>, &#x2026;, s<sub>n</sub>] <=> [s<sub>1</sub>] + s<sub>rest</sub>
        -   s<sub>all</sub>, s<sub>rest</sub> は集合を表すリスト(データ構造)
        -   s<sub>1</sub>, &#x2026;, s<sub>n</sub> は 集合の要素
        -   [s<sub>1</sub>]は，要素 s<sub>1</sub> だけから成る 集合 (リスト)
        -   s<sub>rest</sub> は [s<sub>2</sub>, &#x2026;, s<sub>n</sub>]
    -   s<sub>1</sub> = s<sub>all</sub>[0] リストの0番目の要素
    -   s<sub>n</sub> = s<sub>all</sub>[-1] 最後の要素
    -   集合の要素数は，len(s<sub>all</sub>)
    -   s<sub>rest</sub> = s<sub>all</sub>[1:-1] s<sub>1</sub> 以外の要素を含む集合

-   再帰的に考える
    -   空集合は，空りすと []
    -   与えられた集合sの全ての部分集合を作る関数 subset(s)
        -   空集合のsubset([]) = []
        -   sの全ての部分集合は，
            
            -   s<sub>restの全ての部分集合と</sub>
            -   s[0]を，s<sub>restの全ての各部分集合に要素として追加した集合の集合</sub>
                を
            -   合併して
            
            できた{集合の集合}

    def subset(s):
        if len(s)==0:
            return [[]]
        else:
            s_rest = s[1:]
            ss = subset(s_rest)
            sss = ss
            for i in range(0,len(ss)):
                sm = [s[0]] + ss[i]
                sss =  sss + [sm]
            return sss
    print(subset([]))
    print(subset([1]))
    print(subset([1,2,3]))
    print(len(subset([1,2,3,4,5,6])))

    [[]]
    [[], [1]]
    [[], [3], [2], [2, 3], [1], [1, 3], [1, 2], [1, 2, 3]]
    64

