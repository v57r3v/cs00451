java c
COMPSCI   753 
COMPUTER SCIENCE 
Algorithms for Massive Data 
SEMESTER TWO, 2022
1          Locality-Sensitive Hashing 
Given   three   documents   S1,   S2   ,   S3    and   a   customized   query   document   q:
S1      =   {0, 1,   2},   S2      =   {0,   3,   4},   S3      =   {1,   3,   4},   q =   {h(y),   3,   4};
h(y)   = y         mod   5.where   y   is   the   ﬁrst   digit   of your   Student   ID.   For   instance,   suppose   my   Stu-   dentID=6xxxxx,   my   query   document   would   be   q=      {1,   3,   4},   where      1      =    (6   mod   5).
1.1          Computing MinHash Signatures 
1.      Generate   the   bit-vector   representation   for   {S1,   S2   ,   S3   ,   q} in   shingle   space {0, 1,   2,   3,   4}.            [2 marks]
2.      Generate   the   MinHash   matrix   for   {S1,   S2   ,   S3   ,   q} using   the   following   four MinHash   functions.                [4 marks]h1   (x) =   (2x +1)            mod   5h2   (x) =   (3x +3)            mod   5h3   (x) =   (x +5)            mod   5
3.      Among the   hash   functions,   h1   ,   h2   ,   h3   , which   one   gives the   true   simulated   permutation?                      [1 mark]
4.      Consider   the   query   q   and   estimate   the   signature-based   Jaccard   similari-   ties:   J(q,   S1   ),   J(q,   S2   ),   and   J(q,   S3   ).               [1 mark]
1.2          Tuning Parameters for rNNS In   our   lecture,   we   have   learnt   to   formulate   the   collision   probability   (i.e.,   S-   curve)   given   the   number   of   bands   b   and   the   number   of   rows   per   band   r   as   follows:   Pr(s)   =   1 − (1   − sr   )b.Consider   three   sets   of   parameters   (r=2,b=10), (r=1,b=10), (r=10,b=50). The collision   probabilities   for   similarity   s   in   range   of   [0,1]   for   each   (r   ,b)   are   pro-   vided   accordingly   as   in   Table   1:
1.   Which   settings   give   at   most   5%   of   false   negatives   for   any   60%-similar   pairs?   Brieﬂy   explain   the   reason.                [3 marks]
2.   Which   settings   give   at   most   20%   of   false   positives   for   any   20%-similar   pairs?   Brieﬂy   explain   the   reason.                  [3 marks]
Table1.:   Collision   Probabilities

1.3          c-Approximate Randomized rNNS 
Consider   a   family   transformation   from   (d1   ,   d2   ,   p1   ,   p2   )-sensitive   to   (d1   ,   d2   , 1 − (1 −   p1(k))L   , 1 −   (1 −   p2(k))L   )-sensitive, where   k and   L refer to the number of hash functions   and   the   number   of hash   tables,   respectively.
1.      Brieﬂy   describe   steps   to   achieve   such   transformation.                                        [4 marks]
2.   What   is   the   expected   impact   on   probability   bounds   after   the   transfor-   mation   with   the   k   and   L,   respectively?            [4 marks]
3.      Consider   hash   table   size   l =   10,   MinHash   functions   k   =   5,   and   534   news   articles.   In   phase   one   hashing,   I   generated   signature   matrix   for   l   times.   In   phase   two   hashing,   I   constructed   LSH   hash   tables   of   size   l   ×   m   (m:   the number of buckets). For   each   hash table   lj,   I   computed   the collision distribution for      all      articles      across      m      =    600    buckets    and    reported    a   heatmap      plot      as      follows      (i.e.,    m:    x-axis,    l:      the      y-axis).    The      values      at (mi,   lj)      is      the      number      of   colliding      articles      at      bucket      mi         and      table      lj   .   What   is   the   summation   of   (mi,   lj) ∀mi      ∈   [0,   599]   for   each   hash   table   lj?   [3 marks]
2          Data Stream Algorithms 
2.1          Bloom Filter 
1.      How   can   Bloom   Filter   improve   the   false   positive   ratio?   Why   does   that   work?                [4 marks]
2.      Suppose   we   have   n   bits   of   memory   available   and   set   S   has   m   members.   Instead of using k hash functions, where each mapping an element to a bit   in the main memory, we   could   divide   the   n   bits   into   k   subarrays   (assume   n is   divisible   by   n),   and   then   use   the   i-th   hash   function,   i ∈   [1,   k],   to   the   i-th   subarray.   As   a   function   of n,   m   and   k,   what   is   the   probability   that   a   bin   has   at   least   one   ball   in   the   new   framework?                   [2 marks]
3.      How   does   the   new   framework   compare   with   using   k   hash   functions   into   a   single   array?            [4 marks]
2.2 Misra-Gries Algorithm 
1.    Given   the   data   stream   below,   perform   the   Misra-Gries   a代 写COMPSCI 753 Algorithms for Massive Data (Exam) SEMESTER TWO, 2022SQL
代做程序编程语言lgorithm   with   k = 3   counters   and   present   the   summary,   including   the   elements   and   its   counter values, when the execution of   the algorithm is ﬁnished.   [2 marks]
S   =   {4,   46, 14,   46,   57,   46,   22,   57}
2.      Recall in Assignment 2, there was a request to   “report the average number   of   times   the   decrement   triggered   by      Misra-Gries   over      a   data   stream”   .   What   expected   number   of times   has   the   Misra-Gries   summary   triggered   the decrementsteps after processing the given stream? Please derive your   answer   as   a   function   of   m   and   k.       [3 marks]
2.3          Count Sketch Algorithm Consider   the   same   data   stream   S   and   hash   functions   below.   Given   the   sign   hash functions below, perform. the Count Sketch algorithm and present the   (i)   hash table,   (ii)   counter matrix,   and   (iii) estimated frequency   of   each   element   in   a   stream   after   processing   all   elements.                                   [10 marks]
h1   (x) = x         mod   3                                                          s1   (x) =   ((2x +1)          mod   3)          mod   2
h2   (x) =   (3x +1)            mod   3                           s2   (x) =   ((3x +2)          mod   3)            mod   2
h3   (x) =   (5x +2)            mod   3                           s3   (x) =   ((4x +2)          mod   3)            mod   2

3          Algorithms for Graphs 
3.1 PageRank 
Given   a   directed   graph   G:

1.      Give the column-stochastic adjacency matrix of   the above graph G.   [2 marks]
2.      Compute the PageRank of   the above graph G   without teleport.   [4 marks]
3.   If teleport is applied, each node has   (1−β) chance to   teleport   to   all   other   nodes.   What   changes   will   be   observed   on   the   ranking   of   the   four   nodes   when   (1 −   β)   increases.   What   if   β   = 0?   Explain   your   answer.    [4 marks]
3.2          Community Detection 
1.      Draw an example graph of   four nodes, on which the three graph cut   criteria   (i.e.,   MinCut,   RatioCut   and   NormalizedCut)   produce   the   same   bi-partitioning.                                            [4 marks]
2.      Compute   the   edge   betweenness   for   each   edge   in   the   graph   below.   Which   edge   is   to   be   removed?                [8 marks]

3.3          Inﬂuence Maximization What is the most probable set of   inﬂuenced nodes by running the Indepen-   dent   Cascade   model   on   the   seed   set   S =   {v1   }?   Explain   your   answer.   (Hint:   Consider   the   probability   of   each   deterministic   sub-graphs.   There   could   be   multiple   deterministic   sub-graphs   that   result   in   the   same   set   of   inﬂuenced   nodes.)                    [8 marks]

4          Recommender Systems 
4.1          Collaborative ﬁltering 
Given   the   following   user-item   interaction   matrix   of 4   users   and   5   items:Apply the user-based collaborative ﬁltering algorithm that considers    the   global   bias   bg,   user   bias   bi(user)      and   item   bias   bj(item)   .   Use   Pearson   correlation   coeﬃcient to compute the user similarities. Give the top-1 recommended item to   user   u3   .  [8 marks]  Note: The   predicted   ratings   should   round   to   one   decimal   place. 
4.2          Factorization Machines 
1.      Explain   the   diﬀerence   between   tensor   decomposition   and   factorization   machines in context-aware recommendation, in terms of the computation   cost   and   the   way   of modeling   correlations   among   features.                [4 marks]
2.    A tourism recommender system is to be upgraded for the support of   travel package recommendations. Each travel package is a non-empty   set   of   landmarks.   Users   can   post   their   ratings   on   a   single   landmark   or   the   whole   travel   package.   The   table   below   shows   all   ratings   exist   in   the   database.
(a)    Describe   a   memory-based   collaborative   ﬁltering   algorithm   that   can   	recommend   new   travel   packages   (e.g.,   {l1   ,   l3   }).                   [2 marks](b)      Convert   each   of   the   above   rating   records   as   an   input   feature   vector   		for   factorization   machines.   Explain   how   factorization   machines   rec-   ommend   new   travel   packages   based   on   your   input   feature   vectors.            [4 marks]
(c)      List one advantage of   factorization machines compared to the memory-   based   collaborative   ﬁltering   algorithm   in   travel   package   recommen-      dation.                                   [2 marks]







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
