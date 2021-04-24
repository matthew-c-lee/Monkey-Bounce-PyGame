# Program-09-Expained

# make screen bigger (5)
This was done by changing the values in "pygame.display.set_mode()" to (1280, 720), increasing it to a 720p resolution.
# make monkey move around the outter edges of the window (10) 
This uses the method _around_edges(). It works by checking if the chimp rectangle is touching a side. If it is, it's velocity is changed to go toward the next side. So it starts at the top, and its velocity is changed to go towards the right. Once it hits the right side, it's velocity is changed to go down and hit the bottom. It does this indefinitely.
# keep score (hits and misses) and display on the screen cleanly and clearly - your design (10)
To display the score, I created a font object initialized with font.render('Score: ' + str(score_value), True, (10,10,10)). This puts the score in the top left of the screen. score_value is initialized to zero and goes up whenever the fist punches a chimp. The same is used for misses, except it increments whenever the player misses the chimp.
# allow user to pause the game (5)
To do this, I enclosed the code that blits everything to the screen in an if statement where if the variable state is running, it will blit, and once the state is set to pause, that code won't run. Then I added code so that whenever the user presses down he escape key (with if event.type == pygame.KEYDOWN:) it will change the state to PAUSE. Once the player presses the spacebar, it changes it back to RUNNING. Escape to pause, space to unpause.
# give user menu option to select various levels (10)

    - easy - like it is                                                                             
    - medium - monkey moves around the edges                                                        
    - harder - monkey moves randomly around the edges (5)                                          
 # hardest - monkey moves randomly in any direction (10)
 Using self.rect.bottom > self.area.bottom, etc. I checked to see if it hit a border. If so, I changed the velocity to go away from each edge. If not, it just gives each velocity value X and Y a random number within a range. Because it was changing direction too often, I did a random value check so it'd only change values every time a random range of ten equaled one, which had the effect of increasing the time between each random velocity change.
# insane - allow multiple monkeys (10)
This required me to create a list of monkeys. To add multiple monkeys, I made a loop where I append each monkey to the list and then the list gets used when putting each on the screen.
# allow user to add an animal which will move in various ways
In my menu, I created a button called Add Animal. On clicking, it opens another screen with the choices of Elephant, Dog, and Cat. Upon clicking one of these, it returns the user's choice and later uses that when the user runs the chimp_game method.
# give them the option to select the way of movement (10)
Upon clicking one of them, it opens another screen asking the user for the type of movement they want. Upon clicking one, it returns the user's choice and uses that when running chimp_game.
# add F of your favorite other animals (other than chimp)
Assuming this means add whatever number of animals the user wants, I implemented it by forwarding each choice to chimp_game and using that when creating each Chimp object, which I added to the chimp_list.
# create or find an image of similar size to the chimp (10)
I found some and changed them for each color.
# allow user to choose different colors for each animal when selected (5)
I did this by adding an additional screen at the end after the user chooses the animal of their choices' movement and prompted the user for their color of choice. Then it returns it and feeds it into the chimp_game. A simple if then statement decides which image to use depending on the user's color choice.
# change the audio for a miss to say "missed" (5)
Done, just had to find an audio clip like that and convert it to .wav and put it in the file.
# add background music, be sure to pause it when the user pauses the game (10)
Done, using pygame.mixer.music.load(os.path.abspath('disco.mp3')) and pygame.mixer.music.play when resumed and .pause when paused. The music used is jungle sounds.
# add your own new feature to the game; more complex and engaging the more points (0 - 20)
I created a bonus mode that the user can select under Change Difficulty. Upon selecting BONUS MODE and starting the game, monkeys of random colors will flood the screen, bouncing off the walls in many different directions, while disco music replaces the normal jungle music. The most difficult part of this was the bouncing_off_walls function, which checks if each chimp is touching a wall. When it touches the left or right walls, the velocity's X value will reverse, causing it to fly off. Same  for the Y value when hitting the top or bottom walls. To achieve the disco monkey colors, I randomized which it would initialize each of them in the loop where it creates them and feeds them into the list. To change the music, I made the game check which mode they chose, and if it was the bonus mode it 
