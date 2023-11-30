import pygame
import sys

# Initialize Pygame
pygame.init()

# Constants
WIDTH, HEIGHT = 800, 600
FPS = 60
BEAN_SIZE = 50
BEAN_COLOR = (255, 255, 0)
FLOOR_COLOR = (0, 128, 0)

# Create the game window
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Floor and Bean Game")
clock = pygame.time.Clock()

# Bean properties
bean_x = WIDTH // 2 - BEAN_SIZE // 2
bean_y = HEIGHT // 2 - BEAN_SIZE // 2
bean_speed = 5

# Game loop
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Handle user input
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and bean_x > 0:
        bean_x -= bean_speed
    if keys[pygame.K_RIGHT] and bean_x < WIDTH - BEAN_SIZE:
        bean_x += bean_speed
    if keys[pygame.K_UP] and bean_y > 0:
        bean_y -= bean_speed
    if keys[pygame.K_DOWN] and bean_y < HEIGHT - BEAN_SIZE:
        bean_y += bean_speed

    # Draw the floor
    screen.fill(FLOOR_COLOR)

    # Draw the bean
    pygame.draw.rect(screen, BEAN_COLOR, (bean_x, bean_y, BEAN_SIZE, BEAN_SIZE))

    # Update the display
    pygame.display.flip()

    # Cap the frame rate
    clock.tick(FPS)class Sandwich:
    def __init__(self, ingredients=[]):
        self.ingredients = ingredients

    def add_ingredient(self, ingredient):
        self.ingredients.append(ingredient)

    def display_sandwich(self):
        print("Your sandwich:")
        for ingredient in self.ingredients:
            print(f"- {ingredient}")

class Sandwich:
    def __init__(self):
        self.ingredients = []

    def add_ingredient(self, ingredient):
        self.ingredients.append(ingredient)

    def make_sandwich(self):
        print("Making a delicious sandwich with the following ingredients:")
        for ingredient in self.ingredients:
            print("- " + ingredient)
        print("Enjoy your sandwich!")

# Create a sandwich instance
my_sandwich = Sandwich()

# Add ingredients
my_sandwich.add_ingredient("Bread")
my_sandwich.add_ingredient("Turkey")
my_sandwich.add_ingredient("Lettuce")
my_sandwich.add_ingredient("Tomato")
my_sandwich.add_ingredient("Mayonnaise")

# Make the sandwich
my_sandwich.make_sandwich()

class Player:
    def __init__(self, name, age, team):
        self.name = name
        self.age = age
        self.team = team
        self.score = 0

    def shoot(self):
        print(f"{self.name} takes a shot!")
        # You can add logic here to determine if the shot is successful
        # For simplicity, let's assume every shot is successful
        self.score += 1
        print(f"{self.name} scores! Current score: {self.score}")

    def pass_ball(self, teammate):
        print(f"{self.name} passes the ball to {teammate}.")

# Create a player instance
player1 = Player("John Doe", 25, "Team A")

# Accessing player attributes
print(f"{player1.name} is {player1.age} years old and plays for {player1.team}.")

# Player actions
player1.shoot(a)
player1.pass_ball("Jane Smith")
class Player:
    def __init__(self, name):
        self.name = name
        self.inventory = []

    def pick_up_item(self, item):
        print(f"{self.name} picks up a {item}.")
        self.inventory.append(item)

    def show_inventory(self):
        print(f"{self.name}'s Inventory:")
        for item in self.inventory:
            print("- " + item)

# Create a player instance
player1 = Player("Adventurer")

# Player picks up items
player1.pick_up_item("Sword")
player1.pick_up_item("Shield")
player1.pick_up_item("Health Potion")

# Display player's inventory
player1.show_inventory(b)
class Player:
    def __init__(self, name):
        self.name = name
        self.location = (0, 0)

    def move(self, direction):
        if direction == "up":
            self.location = (self.location[0], self.location[1] + 1)
        elif direction == "down":
            self.location = (self.location[0], self.location[1] - 1)
        elif direction == "left":
            self.location = (self.location[0] - 1, self.location[1])
        elif direction == "right":
            self.location = (self.location[0] + 1, self.location[1])
        else:
            print("Invalid direction. Choose 'up', 'down', 'left', or 'right'.")

    def look_around(self):
        print(f"{self.name} is currently at location {self.location}.")
        print(f"{self.name} looks around.")

# Create a player instance
player1 = Player("Explorer")

# Player moves around
player1.move("up")
player1.move("right")

# Player looks around
player1.look_around(1)
