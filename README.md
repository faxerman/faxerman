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
class ArenaMap:
    def __init__(self, width, height):
        self.width = width
        self.height = height
        self.map_data = [['.' for _ in range(width)] for _ in range(height)]

    def display_map(self):
        for row in self.map_data:
            print(" ".join(row))

    def place_obstacle(self, x, y):
        if 0 <= x < self.width and 0 <= y < self.height:
            self.map_data[y][x] = 'X'
            print(f"Obstacle placed at ({x}, {y}).")
        else:
            print("Invalid coordinates for placing an obstacle.")

def main_menu():
    print("Welcome to the Arena!")
    print("1. View Arena Map")
    print("2. Place Obstacle on Arena Map")
    print("3. Exit")

def navigate_menu(arena):
    while True:
        main_menu()
        choice = input("Enter your choice (1-3): ")

        if choice == '1':
            print("\nArena Map:")
            arena.display_map()
        elif choice == '2':
            x = int(input("Enter X coordinate for the obstacle: "))
            y = int(input("Enter Y coordinate for the obstacle: "))
            arena.place_obstacle(x, y)
        elif choice == '3':
            print("Exiting the Arena. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 3.")

if __name__ == "__main__":
    arena = ArenaMap(width=5, height=5)
    navigate_menu(arena)
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
import random

class Sword:
    def __init__(self, name, damage_range):
        self.name = name
        self.damage_range = damage_range

    def attack(self):
        damage = random.randint(*self.damage_range)
        print(f"{self.name} performs an attack and deals {damage} damage!")
        return damage

# Example usage
if __name__ == "__main__":
    # Create a sword with a damage range
    sword_of_might = Sword("Sword of Might", (10, 20))

    # Perform attacks
    total_damage = 20
    for _ in range(5):
        damage_dealt = sword_of_might.attack()
        total_damage += damage_dealt

    print(f"\nTotal damage dealt: {tclass Player:
    def __init__(self, name, max_health, max_stamina):
        self.name = name
        self.max_health = max_health
        self.max_stamina = max_stamina
        self.health = max_health
        self.stamina = max_stamina

    def display_status(self):
        print(f"{self.name}'s Status:")
        print(f"Health: {self.health}/{self.max_health}")
        print(f"Stamina: {self.stamina}/{self.max_stamina}")

    def take_damage(self, damage):
        self.health -= damage
        if self.health < 0:
            self.health = 0
        print(f"{self.name} takes {damage} damage!")

    def perform_attack(self, sword):
        if self.stamina >= 5:
            self.stamina -= 5
            damage_dealt = sword.attack()
            print(f"{self.name} performs an attack and consumes 5 stamina.")
            return damage_dealt
        else:
            print(f"{self.name} does not have enough stamina to perform an attack!")
            return 0

    def rest(self):
        self.stamina += 10
        if self.stamina > self.max_stamina:
            self.stamina = self.max_stamina
        print(f"{self.name} rests and recovers 10 stamina.")

# Example usage
if __name__ == "__main__":
    player1 = Player("Hero", max_health=100, max_stamina=50)
    sword_of_might = Sword("Sword of Might", (10, 20))

    # Display initial status
    player1.display_status()

    # Player takes damage
    player1.take_damage(15)
    player1.display_status()

    # Perform attacks
    total_damage = 0
    for _ in range(3):
        total_damage += player1.perform_attack(sword_of_might)

    # Rest to recover stamina
    player1.rest()
    player1.display_status()

import random

class Sword:
    def __init__(self, name, damage_range):
        self.name = name
        self.damage_range = damage_range

    def attack(self):
        damage = random.randint(*self.damage_range)
        print(f"{self.name} performs an attack and deals {damage} damage!")
        return damage

class Shield:
    def __init__(self, name, block_chance):
        self.name = name
        self.block_chance = block_chance

    def block_attack(self):
        if random.random() < self.block_chance:
            print(f"{self.name} successfully blocks the attack!")
            return True
        else:
            print(f"{self.name} fails to block the attack.")
            return False

class Player:
    def __init__(self, name, max_health, max_stamina):
        self.name = name
        self.max_health = max_health
        self.max_stamina = max_stamina
        self.health = max_health
        self.stamina = max_stamina
        self.sword = Sword("Sword of Might", (10, 20))
        self.shield = Shield("Iron Shield", block_chance=0.5)

    def display_status(self):
        print(f"{self.name}'s Status:")
        print(f"Health: {self.health}/{self.max_health}")
        print(f"Stamina: {self.stamina}/{self.max_stamina}")

    def take_damage(self, damage):
        self.health -= damage
        if self.health < 0:
            self.health = 0
        print(f"{self.name} takes {damage} damage!")

    def perform_attack(self):
        if self.stamina >= 5:
            self.stamina -= 5
            damage_dealt = self.sword.attack()
            print(f"{self.name} performs an attack and consumes 5 stamina.")
            return damage_dealt
        else:
            print(f"{self.name} does not have enough stamina to perform an attack!")
            return 0

    def block_attack(self):
        return self.shield.block_attack(10)

    def rest(self):
        self.stamina += 10
        if self.stamina > self.max_stamina:
            self.stamina = self.max_stamina
        print(f"{self.name} rests and recovers 10 stamina.")

# Example usage
if __name__ == "__main__":
    player1 = Player("Hero", max_health=100, max_stamina=50)

    # Display initial status
    player1.display_status(block)

    # Perform attacks and shield blocks
    total_damage = 0
    for _ in range(3):
        damage_dealt = player1.perform_attack()
        if not player1.block_attack():
            player1.take_damage(damage_dealt)
        total_damage += damage_dealt

    # Rest to recover stamina
    player1.rest(block)
    player1.display_status(block)

    print(f"\nTotal damage dealt: {total_damage}")    print(f"\nTotal damage dealt: {total_damage}")otal_damage}")
