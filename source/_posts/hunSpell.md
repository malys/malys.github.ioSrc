title: HunSpell
categories:
	- Technologie
tags:
	- ConEmu
	- Astuce
---

http://hunspell.sourceforge.net/




http://xahlee.blogspot.fr/2010/06/hunspell-tutorial.html


Add a Hunspell dictionary

Download the required Spelling or Hyphenation dictionary. The downloaded file has an oxt extension (when downloaded from OpenOffice site). If you download it from a site other than OpenOffice, the extension can be different.

Change the filename extension to zip. For example, rename xyz.ext to anyname.zip.

Extract the contents of the zip archive to a folder and locate an affix (.aff) file, a spelling dictionary (.dic) file or a hyphenation dictionary (.dic) file. Rename these files using the language ISO codes as given in the table below.

Language ISO codes are of the form: <ISO 639-1 language codes in lower case>_<CountryCode in upper case>. For example, English (United States) is en_US.

File type
Rename to
Example
aff file
<language ISO Code>.aff
 en_US.aff
Spelling dictionary
<language ISO Code>.dic
 en_US.dic
Hyphenation dictionary	hyph_<language ISO Code>.dic	 hyph_en_US.dic
For a list of ISO 639-1 language codes, see http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes
For a list of Country codes, see http://www.iso.org/iso/country_names_and_code_elements

Create a folder named <language ISO Code> in the Dictionaries folder, and copy these renamed files in it. Depending on the operating system, you can find the directory "Dictionaries" at the locations listed below.