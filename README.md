# LZ4++
## A very simple wrapper for LZ4, in modern C++

I had a few headaches trying to use LZ4 with modern C++, mostly bounding issues with the null termination byte.

Finally figured it out, and hopefully it'll solve headaches for at least another person out there.

## Requirements
`lz4`

## Usage
Plain Text:
```cpp
const std::string text = "sometimes butterflies sing to me in my sleep sometimes butterflies sing to me in my sleep sometimes butterflies sing to me in my sleep sometimes butterflies sing to me in my sleep sometimes butterflies sing to me in my sleep";
const std::string compressed = lz4::compress(text);

// no need to worry about accounting for the null termination byte
const std::string decompressed = lz4::decompress(compressed, text.size());

if (decompressed == text) {
  std::cout << "LESS GOOOOO\n";
}
else {
  std::cout << "aw.\n";
}
```

Binary:
```cpp
const std::string binary = "some binary data";
const std::string compressed = lz4::compress<lz4::format::bin>(binary);
const std::string decompressed = lz4::decompress<lz4::format::bin>(compressed, binary.size());

if (decompressed == text) {
  std::cout << "machine mode bzzt\n";
}
else {
  std::cout << "darn\n";
}
```
