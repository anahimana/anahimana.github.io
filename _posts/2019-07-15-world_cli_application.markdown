---
layout: post
title:      "World CLI Application"
date:       2019-07-15 10:18:22 -0400
permalink:  world_cli_application
---

I set out to build a Ruby command line application (CLI) that someone can use to learn information about the world. This CLI scrapes the [CIA World Factbook](https://www.cia.gov/library/publications/the-world-factbook/index.html)  website and planets from [Wikipedia](https://en.wikipedia.org/wiki/Solar_System).

## Getting Started with the project
As novice, I fully understand how hard it can be to get started. Here are some steps I took.

1. Define some basic things about your program
2. Set up your programming environment
3. Commit, commit, and commit some more...

### Defining basics of your program
For this, I decided on the following basic functionality
* Show a list of country
* Show general information about the world
* Show a list of planets in our solar system

Putting all of together, the user should be greeted with something like this.

You are greeted and given a menu
```
Welcome the World!
What would you like to do?
Enter '1' to see list of countries.
Enter '2' to see general information about the world.
Enter '3' to see list of planets.
Enter '4' to see to exit the program.
```
*Option 1* should give you a list of all the countries.
```
1. Akrotiri
2. Albania
3. Algeria
4. American Samoa
5. Andorra
6. Angola
7. Anguilla
8. Antarctica
9. Antigua and Barbuda
10. Arctic Ocean
11. Argentina
12. Armenia
13. Aruba
14. Ashmore and Cartier Islands
15. Atlantic Ocean

...
```
*Option 2* Should give you information about the world.
```
Background : Globally, the 20th century was marked by: (a) two devastating world wars; (b) the Great Depression of the 1930s; (c) the end of vast colonial empires; (d)
rapid advances in science and technology, from the first airplane flight at Kitty Hawk, North Carolina (US) to the landing on the moon; (e) the Cold War between the Wes
tern alliance and the Warsaw Pact nations; (f) a sharp rise in living standards in North America, Europe, and Japan; (g) increased concerns about environmental degradat
ion including deforestation, energy and water shortages, declining biological diversity, and air pollution; (h) the onset of the AIDS epidemic; and (i) the ultimate eme
rgence of the US as the only world superpower. The planet's population continues to explode: from 1 billion in 1820 to 2 billion in 1930, 3 billion in 1960, 4 billion i
n 1974, 5 billion in 1987, 6 billion in 1999, and 7 billion in 2012. For the 21st century, the continued exponential growth in science and technology raises both hopes
(e.g., advances in medicine and agriculture) and fears (e.g., development of even more lethal weapons of war).

Climate : a wide equatorial band of hot and humid tropical climates, bordered north and south by subtropical temperate zones that separate two large areas of cold and d
ry polar climates

Popuplation : 7,503,828,180

Languages : Mandarin Chinese 12.3%, Spanish 6%, English 5.1%, Arabic 5.1%, Hindi 3.5%, Bengali 3.3%, Portuguese 3%, Russian 2.1%, Japanese 1.7%, Punjabi, Western 1.3%,
Javanese 1.1% (2018 est.)
note 1: percents are for "first language" speakers only; the six UN languages - Arabic, Chinese (Mandarin), English, French, Russian, and Spanish (Castilian) - are the
mother tongue or second language of about 45% of the world's population, and are the official languages in more than half the states in the world; some 400 languages ha
ve more than a million first-language speakers
note 2: all told, there are an estimated 7,100 languages spoken in the world; approximately 80% of these languages are spoken by less than 100,000 people;

...
```

*Option 3* Should give a list of all the planets
```
Here is a list of all planets...
1. Mercury
2. Venus
3. Earth
4. Mars
5. Jupiter
6. Saturn
7. Uranus

```


### Set up programming environment

For this project, I used [Bundler](https://bundler.io/v2.0/guides/creating_gem.html) to setup the importand files and directories for my program.

### Commit, commit, and commit some more...

As programmers, we may easily lose track of what were doing. It is important, I think (most would agree), to commit as much as possible. I have learned the hard way of useful Git versioning can be. So every time I add or remove something that impacts my program, I stage it and/or commit it. It helps keep track of your work and save you when things go wrong down the road.

If you used Bundler to generate your project files, then you should be able to `git commit -m "Initial Commit`. If not, you can follow this example from [Git Documentation](https://git-scm.com/docs/git-init#_examples).

```
Start a new Git repository for an existing code base

$ cd /path/to/my/codebase
$ git init      (1)
$ git add .     (2)
$ git commit    (3)

Create a /path/to/my/codebase/.git directory.
Add all existing files to the index.
Record the pristine state as the first commit in the history.

```

Once you are ready to share your work, you can host repository on github. Here is a nice article on how to do that. [How to create a repository](https://help.github.com/en/articles/create-a-repo).

If you find this post useful, then great. If not, how can I make it useful to you as the reader? Here is link to my [repository](https://github.com/anahimana/world-cli).

