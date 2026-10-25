# MapReduce Word Count

Name: Nadine Hassan
Student ID: 231005869

## What it does
A small MapReduce engine in Python (no Hadoop, no Spark). It has these phases:
1. Input: a folder of text files, each file is one split
2. Map: emits (word, 1) for every word
3. Mappers run at the same time, one per split (threads)
4. Combine + Partition: local subtotals, then each word goes to one of 2 reducers
5. Shuffle & Sort, then Reduce: sums the values and writes one output file per reducer

## How to run
1. Open `mapreduce.ipynb` in Jupyter or Google Colab
2. Run the cells from top to bottom
3. Output files are written to the `out/` folder (`part-0.txt`, `part-1.txt`)

## Sample input
['note1.txt', 'note2.txt', 'note3.txt']

## Sample output
os.makedirs(IN_DIR, exist_ok=True)
samples = {
    "note1.txt": "car damage fire roof",
    "note2.txt": "theft car water damage",
    "note3.txt": "fire roof water car",
}
for name, text in samples.items():
    with open(os.path.join(IN_DIR, name), "w") as f:
        f.write(text)
print(os.listdir(IN_DIR))

