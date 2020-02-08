# Junior Developer Resume

## Vladislav Zheromsky

### Contact Info
* *E'mail:* vladislavzheromsky@gmail.com
* *Mobile phone number (Telegram, Viber):* 8-044-713-61-85
* *GitHub:* [zheromskyV](https://github.com/zheromskyV)

### Summary
I am curious, enthusiastic, disciplined, tolerant and friendly. Also I'm a hardworker and quick learner who has allways been keen on studying.  Time management, decision-making and prioritizing are the things I am really good at. My persistence, good analytical skills and stress-tolerance make me a reliable person.

### Skills
* C/C++, HTML, CSS
* Have knowledge of object-oriented and procedural programming

### Code examples
Here is a code example of a *Cryptographer* class in C++:

```
// Cryptographer.h
#pragma once

#include <string>
#include <array>

class Cryptographer
{
public:
	static void init();

	static void encrypt(std::string& str);
	static void decrypt(std::string& str);

private:
	Cryptographer() = delete;
	enum class CryptoMode { ENCRYPT, DECRYPT };

	static std::array<char, 159> alphabet;
	static const std::array<int, 5> key;

	static int findPos(const char c);

	static void gronsfeld(std::string& str, CryptoMode mode);
};
```
```
// Cryptographer.cpp
#include "Cryptographer.h"
#include <array>

using namespace std;

const array<int, 5> Cryptographer::key = { 9, 17, 4, 11, 3 };
array<char, 159> Cryptographer::alphabet = {};

void Cryptographer::encrypt(string& str)
{
	gronsfeld(str, CryptoMode::ENCRYPT);
}

void Cryptographer::decrypt(string& str)
{
	gronsfeld(str, CryptoMode::DECRYPT);
}

// initialize alphabet with chars for Eng and Rus
void Cryptographer::init()
{
	int i, j;
	for (i = -1, j = 0; i >= -64; i--) {
		if (j < alphabet.size())
			alphabet[j++] = i;
	}
	for (i = 32; i <= 126; i++) {
		if (j < alphabet.size())
			alphabet[j++] = i;
	}
}

// returns char's position in the alphabet
int Cryptographer::findPos(const char c)
{
	int pos = -1;
	for (int j = 0; j < alphabet.size(); j++) {
		if (alphabet[j] == c) {
			pos = j;
			break;
		}
	}
	return pos;
}

// algorithm for encryption and decryption
void Cryptographer::gronsfeld(string& str, CryptoMode mode)
{
	short coder = mode == CryptoMode::ENCRYPT ? 1 : -1;

	int begin = 0; // alphabet's head
	int end = alphabet.size() - 1; // alphabet's tail

	// iterate through the string
	for (size_t i = 0; i < str.size(); i++) {
		// define the offset based on the key and mode
		int offset = key[i % 5] * coder;
		// define char current position in the alphabet
		int pos = findPos(str.at(i));

		// define new char position based on the current position ang the offset
		int newPos = -1;
		if (pos + offset > end) {
			int dif = pos + offset - end;
			newPos = begin + dif;
		}
		else if (pos + offset < begin) {
			int dif = pos + offset + begin;
			newPos = end + dif;
		}
		else {
			pos += offset;
			newPos = pos;
		}

		// replace the char
		str.at(i) = alphabet[newPos];
	}
}
```

### Experience
* Course project ***'The accounting of clients of a paid clinic'*** using *procedural programming* and *C* 
* Course project ***'The development of the automated system for the patient accounting'*** using *object-oriented programming* and *C++*

### Education
* Currently studying (from 2018) at *Belarusian State University of Informatics and Radioelectronics* in the speciality ***'Information Systems and Technologies (in Economics)'***
* Completed ***HTML+CSS basics courses*** from *HTML Academy* in 2020
* Completed ***Business School 'From Idea to Business'*** in 2017

### English
*__B2 level__ (CEFR)*
