# Testing & RSpec

# Before Using Better Tests 

```
require_relative('../pig_latin')
#pig_latin_spec.rb
describe 'Converting single words to Pig Latin' do
  it "converts a word" do
    expect(convert('the').should eq('ethay'))
    expect(convert('Over').should eq('over'))
    expect(convert('Slack').should eq('ackslay'))
  end
end

describe 'Converting a sentence should Pig Latin' do
  it "converts a sentence" do
    expect(convert('The dog jumped over the lake').should eq('ethay ogday umpedjay over ethay akelay'))
  end
end
```

```
#pig_latin.rb
require 'pry'
def convert_word(word)
  word.downcase!
  p word
  return word if word.match(/(^[AEIOU]+)/i)
  consonants = word.match(/(^[^AEIOU]+)/i).captures[0]
  word.slice!(0,consonants.length)
  word + consonants + 'ay'
end

def convert(words)
  string = ''
  words.split(' ').each do |word|
    string << convert_word(word) + ' '
  end
  string.rstrip
end
```

# After Spec

```
# pig_latin.rb
def convert_word(word)
  word.downcase!
  return word if starts_with_vowel?(word)
  cons = consonants(word)
  word.slice!( 0,cons.length )
  append_consonants_and_ay(word,cons)
end

def consonants(word)
  word.match(/(^[^AEIOU]+)/i).captures[0]
end

def append_consonants_and_ay(word,consonants)
  word + consonants + 'ay'
end

def starts_with_vowel?(word)
  word.match(/(^[AEIOU]+)/i)
end

def convert(words)
  string = ''
  words.split(' ').each do |word|
    string << convert_word(word) + ' '
  end
  string.rstrip
end
```

```
# pig_latin_spec.rb
require_relative('../pig_latin')

# CONVERT SINGLE WORD

# IF the word starts with a vowel, return the word.
#     ELSE return the word's pig latin equivalent.
#   MOVE all leading consonants to the end of the word
#   and add the suffix "ay."
# ENDIF

# CONVERT COMPLETE SENTENCE
#
# FOR each word in the sentence.
#     CONVERT SINGLE WORD
# ENDFOR
# RETURN converted sentence

describe '#consonants' do
  it "get's all consonants until the first vowel" do
    expect(consonants('platypus').should eq('pl'))
  end
end


describe '#append_consonants_and_ay' do
  it "appends letters + ay to the end of a word" do
    expect(append_consonants_and_ay('Zebra','letters')).to eq('Zebralettersay')
  end
end

describe '#starts_with_vowel?' do
  it "returns matchdata if a letter starts with a vowel" do
    expect(starts_with_vowel?('about')).to be_instance_of(MatchData)
  end

  it "returns nil if a letter does not start with a vowel" do
    expect(starts_with_vowel?('booo')).to be(nil)
  end
end

describe '#convert_word' do
  it "does NOT convert a word that starts with a vowel" do
    expect(convert('Over').should eq('over'))
  end

  it "DOES convert a word that starts with a consonant" do
    expect(convert('dog').should eq('ogday'))
  end

end

describe '#convert' do
  it "converts a sentence" do
    expect(convert('The dog jumped over the lake').should eq('ethay ogday umpedjay over ethay akelay'))
  end
end

```


