# Huffman Coding (Greedy)

## Theory
* **Goal:** Lossless data compression by assigning **variable-length prefix-free binary codes** to characters based on their frequencies—frequent characters get shorter codes, rare characters get longer codes.
* **Prefix-Free Rule:** No code is a prefix of another code (ensured by placing characters strictly at the **leaves** of a binary tree), allowing unambiguous decoding.
* **Greedy Strategy:** Repeatedly extract the two nodes with the **lowest frequencies** from a Min-Heap, merge them into a new internal node with frequency `f1 + f2`, and re-insert into the Min-Heap until one root remains.

## Algorithm
```text
HuffmanCoding(chars, freq, n):
  Create a Min-Heap H of n leaf nodes (char, freq)
  while H.size() > 1:
    left = H.extractMin()
    right = H.extractMin()
    merged = new Node('$', left.freq + right.freq)
    merged.left = left
    merged.right = right
    H.insert(merged)
  root = H.extractMin()
  Assign '0' to left edges and '1' to right edges from root to leaves
```

## Complexity
* **Time Complexity:** `O(n log n)` *(`n - 1` heap extractions and insertions, each `O(log n)`)*
* **Space Complexity:** `O(n)` for the Min-Heap and Huffman tree (`2n - 1` nodes).
