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
    clock.tick(FPS)
