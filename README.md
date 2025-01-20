# MongoDB Aggregation Pipeline Bug: Incorrect $inc Operator Placement

This repository demonstrates a common error when using the `$inc` operator within a MongoDB aggregation pipeline. The `$inc` operator is intended to increment numeric fields, but it's misused in this example, leading to unexpected results.

## Problem
The original code attempts to increment the `sum` field after projection in the aggregation pipeline. However, this is not allowed because the aggregation pipeline stages operate sequentially, and `$inc` cannot be used after the `$project` stage to modify a newly generated field like `sum`.

## Solution
The solution involves applying the `$inc` operator within the `$group` stage, correctly accumulating the values.

## How to reproduce
1. Clone the repository.
2. Run `mongo`.
3. Use the code snippets provided in `bug.js` and `bugSolution.js` to create your test collection and run the aggregation pipeline.
4. Compare the results of both versions to observe the incorrect and correct behavior.

## Contributing
Feel free to contribute by identifying additional common errors or providing more effective solutions.