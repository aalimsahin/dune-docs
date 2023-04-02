[View code on GitHub](https://dune.com/docs/query/DuneSQL-reference/SQL-statement-syntax/pattern-recognition-in-window.md)

This technical guide covers the topic of row pattern recognition in window structures for the Dune Docs project. The guide explains how to define a window frame with row pattern recognition, which involves many syntactical components, mandatory or optional, and enforces certain limitations on the frame extent. The guide also describes the pattern recognition clauses, including the `PATTERN` and `DEFINE` clauses, which specify a row pattern and define the row pattern primary variables in terms of boolean conditions that must be satisfied. 

The `MEASURES` clause is also explained, which is syntactically similar to the `MEASURES` clause of `MATCH_RECOGNIZE`. However, the semantics of this clause differs between `MATCH_RECOGNIZE` and window. The `AFTER MATCH SKIP` clause, `INITIAL` or `SEEK` modifier, and `SUBSET` clause are also covered in detail. 

The guide then explains how pattern recognition in window processes input rows in two different cases: upon a row pattern measure call over the window and upon a window function call over the window. The output row produced for each input row consists of all values from the input row and the value of the called measure or window function, computed with respect to the pattern match associated with the row. 

Finally, the guide covers empty matches and unmatched rows. An empty match is a successful match that does not involve any pattern variables, while an unmatched row is a row for which no match can be found. The guide explains that in most cases, the results for empty matches and unmatched rows are the same, but a constant measure can be helpful to distinguish between them. 

Overall, this guide provides a detailed explanation of row pattern recognition in window structures, including the syntax and semantics of the various clauses involved, and how input rows are processed with pattern recognition.
## Questions: 
 1. What is the difference between row pattern recognition in window structures and in `MATCH_RECOGNIZE`?
- The app technical guide explains that in window structures, the pattern matching can neither match rows nor retrieve input values outside the frame, unlike in `MATCH_RECOGNIZE` where the pattern search can explore all rows until the partition end, and all rows of the partition are available for computations.

2. What are the limitations of the `frame_extent` in a window frame with row pattern recognition?
- The `frame_extent` with row pattern recognition must be defined in terms of `ROWS`, and the frame start must be at the `CURRENT ROW`, which limits the allowed frame extent values to `ROWS BETWEEN CURRENT ROW AND CURRENT ROW`, `ROWS BETWEEN CURRENT ROW AND <expression> FOLLOWING`, and `ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING`.

3. Can you specify `ONE ROW PER MATCH` or `ALL ROWS PER MATCH` in window structures?
- No, you cannot specify `ONE ROW PER MATCH` or `ALL ROWS PER MATCH` in window structures because all calls over window, whether they are regular window functions or measures, must comply with the window semantics, which is supposed to produce exactly one output row for every input row. The output mode of pattern recognition in window is a combination of `ONE ROW PER MATCH` and `WITH UNMATCHED ROWS`.