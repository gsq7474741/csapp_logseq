query-table:: false
#+BEGIN_QUERY
{:title "reference of datalog"
 :query [:find (pull ?b [*])
         :in $ ?tag
         :wher
         (page-ref ?b ?tag)]
 :inputs ["card"]}
#+END_QUERY

- query-sort-by:: block
  query-table:: false
  query-sort-desc:: false
  #+BEGIN_QUERY
  {:title ["cards from chapter 2 信息的表示和处理"]
   :query [:find (pull ?b [*])
           :where
           [?p :block/name "card"]
           [?b :block/refs ?p]]}
  #+END_QUERY
-
- query-table:: true
- /zotero
  query-table:: false
-