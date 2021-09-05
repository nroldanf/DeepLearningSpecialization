# 

## Error analysis

This gives you a sense on which approach to pursue when you are looking to improve performance.

If you are trying to develop an algorithm that make what humans do, and if its not yet at the performance of a human, then manually examining errors that your algorithm is making, can give you insights in what to do next.

Is worth an effor to fix misclassification errors?

__Idea__

1. Get ~100 mislabeled dev set examples.
2. Count up how many are the problematic label.

- Analyze the proportion of the misclassified label to see what will happen if you design something to better classify this label with the general error. Depending on this, you can decide if spending time on improving performance for this label.

The key point is deciding in which direction go to do the effort actually worth.

You can evaluate multiple ideas en parallel, using kind of spreadsheet analysis and commenting on describing the example that was misclassified. With this, you can decide which is your main problem and in what to focus. With this, different persons on a team can focus on different things.

You can add more columns to this spreadsheet to give you an estimate on how it behaviors on this category of error.

1. __Cleaning Out error analysis__

Sometimes examples are mislabeled, which can affect on how the functionn is mapping x to y.

Deep Learning algorithms are robust to this kind of random errors if the total percentage of errors is not too high, but less robust to systematic errors (e.g. labeled white dogs as white cats).

You can add this incorrectly labeled as a column to error analysis.

2. __Build your first system quicly then iterate__


