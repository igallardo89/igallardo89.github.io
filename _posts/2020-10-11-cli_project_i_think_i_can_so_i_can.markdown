---
layout: post
title:      "CLI Project.. I think I can.. so I can"
date:       2020-10-11 18:45:50 +0000
permalink:  cli_project_i_think_i_can_so_i_can
---



We were asked to create our first project after 6 weeks of our Software Engineering Program at Flatiron School. It's safe to say the beginning of the program is very much the beginning of my entire coding career. The weeks began creeping on the project slowly, where my nervousness and fear would heighten as it got closer. We had just began the lessons on retrieving data either via Scraping or from a public API.  I remember thinking to myself, there should be a couple of lessons to completely getting it before- hence enters the project. Create a Command Line Interface (CLI) application, where we provide the user a choice to which would lead to relevant information pulled from our Public API.

Ok, so what do I want my project to be? I shortly after found a public API provided by Score Bat for soccer highlights. How perfect, being raised with a fanatic futbol family and engaged to a die hard Inter Milan fan I thought it would be great and "fun"  to build on this. Giving the short list (due to COVID) of leagues around the world and then  providing the user the option to choose a game and then get its highlights. OK! Perfect, lets do this.

Show me the API.... ok... wait... this isn't going to be easy. I must've hit errors for the first 5 days. Constantly trying to figure out what the errors were telling me and why I couldn't pull the data I wanted.  APIs weren't being as kind as I hoped they would be and I just wasn't sure about what I was doing incorrectly . I remembered what the Flatiron Orientation Education Coach Valerie Jiggetts said about feeling like hitting the bottom from time to time. I ignorantly believed - ehh, how bad could that be? This was the bottom, what was I doing here? Why am I coding? I don't know why I decided to start coding. But then thats it... Ok but what am I doing here? What am I trying to actually make happen in my code? I started to re-evaluate my code, and realized I was mostly trying to go step by step what I had seen others were doing or what was taught. But what if I just tried to get the code to run, maybe that meant just on my terms and that might be good enough. 

Flatiron School makes it really clear how much googling and research is need in this field and maybe I was a little stubborn in accepting that. So here I was ... I must've watched 1000000x Youtube videos, rewatched lectures about 3x each, trying different codes, ok ... let me try this.

```
   @competitions = API.fetch_competition(@competition)
	 leagues = @competitions.map{ |competition| competition["competition"]["name"] }.map { |name|  name.match(/(^.*):/)[1] }.uniq.sort
        leagues.each do |league|
        puts "#{league}"
```

In one of the BONUS lessons Rubular is introduced and I have been stuck on how to split : the name to be more accessible so I decided to try it. Hence it provided me with: 
``` 
/(^.*):/)
```

This piece of code(RegEx) was providing me with the ability to dissect the name in the API and calling back only [1].

This would finally push me forward in getting the names of countries in a list and with a .uniq.sort, it was organized now.

"Welcome to Game Highlights!
 
Look below for the current Leagues happening:
 
* BELARUS
* CHINESE TAIPEI
* ENGLAND
* EUROPA LEAGUE
* FRANCE
* GERMANY
* ITALY
* KOREA REPUBLIC
* POLAND
* RUSSIA
* SPAIN
* UKRAINE
* WORLD
* WORLD CUP"

Now I would want each one of the countries if chosen to return back a list of games. Using the instance method with an argument of the users inp to bring those games back.

```
def find_games(inp)
       @competitions.map { |competition| competition if competition["competition"]["name"].start_with?(inp) }
   end
```

The method ask for the map/collect of @competition and if the users input matches using start_with?  the competition name it pull would pull that particular league up. Which would lead to now pulling the titles from the competition/league to the games in each. 
```
games = find_games(inp)
         puts "Game Matches:"
         puts ""
         game_titles = games.map { |game| game ["title"] }
         game_titles.each_with_index do |game_title, i|
         puts "#{i+1}:#{game_title}"
         end 
```

There you have it, from then it was just adding a little more code to getting the url for Highlights of each games.
I will say I walk away from this CLI a bit exhausted but grateful. The exhaustion is really worth it because I know I'm learning something completely new and when it works it really feels like fireworks! 'm excited for what the rest of my education and career has in store. As Valerie said... from the bottom, it always goes back up. 


