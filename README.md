import tkinter as tk
import random

class Player:
    # (unchanged)

class Bot:
    def __init__(self, canvas, x, y, radius, color):
        self.canvas = canvas
        self.id = canvas.create_oval(x - radius, y - radius, x + radius, y + radius, fill=color)
        self.x_speed = 0
        self.y_speed = 0

    def move_towards_player(self, player):
        player_x, player_y = self.canvas.coords(player.id)
        bot_x, bot_y = self.canvas.coords(self.id)
        angle = atan2(player_y - bot_y, player_x - bot_x)
        self.x_speed = 2 * cos(angle)
        self.y_speed = 2 * sin(angle)

    def move_randomly(self):
        self.x_speed = random.choice([-2, 2])
        self.y_speed = random.choice([-2, 2])

    def move(self):
        self.canvas.move(self.id, self.x_speed, self.y_speed)

class ArenaMap:
    # (unchanged)

class Game:
    def __init__(self, root, width, height):
        # (unchanged)
        self.bot = Bot(self.canvas, width // 4, height // 4, 20, "red")
        self.animate()

    def animate(self):
        # (unchanged)
        self.bot.move_towards_player(self.arena_map.player)
        self.bot.move_randomly()  # Simulate random movement for simplicity
        self.bot.move()

# Rest of the code (unchanged)
# ...

# Run the Tkinter event loop
import tkinter as tk
import random

class Player:
    def __init__(self, canvas, x, y, radius, color):
        self.canvas = canvas
        self.id = canvas.create_oval(x - radius, y - radius, x + radius, y + radius, fill=color)
        self.x_speed = 0
        self.y_speed = 0

    def move(self):
        self.canvas.move(self.id, self.x_speed, self.y_speed)

class ArenaMap:
    def __init__(self, canvas, width, height):
        self.canvas = canvas
        self.width = width
        self.height = height
        self.player = Player(canvas, width // 2, height // 2, 20, "blue")
        self.gun_location = (random.randint(30, width - 30), random.randint(30, height - 30))
        self.gun_picked_up = False
        self.gun_id = None

    def display_map(self):
        if not self.gun_picked_up:
            if not self.gun_id:
                self.gun_id = self.canvas.create_rectangle(
                    self.gun_location[0] - 10, self.gun_location[1] - 10,
                    self.gun_location[0] + 10, self.gun_location[1] + 10, fill="green"
                )

    def pick_up_gun(self):
        if not self.gun_picked_up and self.gun_location[0] - 20 < self.player.x_speed < self.gun_location[0] + 20 \
                and self.gun_location[1] - 20 < self.player.y_speed < self.gun_location[1] + 20:
            self.gun_picked_up = True
            self.canvas.delete(self.gun_id)
            print("You picked up the gun!")

# Game class that manages the main loop
class Game:
    def __init__(self, root, width, height):
        self.root = root
        self.width = width
        self.height = height
        self.canvas = tk.Canvas(root, width=width, height=height)
        self.canvas.pack()
        self.arena_map = ArenaMap(self.canvas, width, height)
        self.root.bind("<Up>", self.move_up)
        self.root.bind("<Down>", self.move_down)
        self.root.bind("<Left>", self.move_left)
        self.root.bind("<Right>", self.move_right)
        self.root.bind("<space>", self.pick_up_gun)
        self.animate()

    def move_up(self, event):
        self.arena_map.player.y_speed = -5

    def move_down(self, event):
        self.arena_map.player.y_speed = 5

    def move_left(self, event):
        self.arena_map.player.x_speed = -5

    def move_right(self, event):
        self.arena_map.player.x_speed = 5

    def pick_up_gun(self, event):
        self.arena_map.pick_up_gun()

    def animate(self):
        self.canvas.delete("all")  # Clear canvas
        self.arena_map.display_map()
        self.arena_map.player.move()
        self.root.after(20, self.animate)  # Repeat the animation after 20 milliseconds

# Create the main window
root = tk.Tk()
root.title("Arena Game")

# Set the dimensions of the window and start the game
game = Game(root, width=400, height=400)

# Run the Tkinter event loop
root.mainloop(100)
