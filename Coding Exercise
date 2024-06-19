import sys,os
os.chdir(sys.path[0])
import matplotlib.pyplot as plt
from wordcloud import WordCloud, STOPWORDS
from collections import Counter

# List of file names
file_names = ["Speech1.txt", "Speech2.txt", "Speech3.txt", "Speech4.txt", "Speech5.txt"]

# Initialize an empty string to store the text
text = ""

# Loop through each file and read its content
for file_name in file_names:
    with open(file_name, "r") as file:
        text += file.read() + " "

# Create a set of stopwords
stopwords = set(STOPWORDS)

# Split the text into words
words = text.split()

# Remove stopwords
words = [word.lower() for word in words if word.lower() not in stopwords]

# Count the frequency of each word
word_freq = Counter(words)

# Remove words that appear only once
word_freq = {word: freq for word, freq in word_freq.items() if freq > 1}

# Calculate the maximum frequency
max_freq = max(word_freq.values())

# Create a dictionary to store the font sizes
font_sizes = {}

# Calculate the font size for each word
for word, freq in word_freq.items():
    if freq == max_freq:
        font_sizes[word] = 'Huge'
    elif freq > 0.6 * max_freq:
        font_sizes[word] = 'Big'
    elif freq > 0.3 * max_freq:
        font_sizes[word] = 'Normal'
    else:
        font_sizes[word] = 'Small'

# Print the words, along with their frequencies and font sizes
print("Words, along with their frequencies and font sizes:")
for word, freq in word_freq.items():
    print(f"{word}: {freq} ({font_sizes[word]})")

# Create a WordCloud object
wc = WordCloud(background_color="white", stopwords=stopwords, height=600, width=400)
wc.generate(text)

# store to file
wc.to_file("wordcloud_output.png")
