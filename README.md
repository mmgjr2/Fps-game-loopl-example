# game_loop.py
import time

# Target FPS
TARGET_FPS = 60
FRAME_TIME = 1 / TARGET_FPS

# Termination condition
game_running = True

# Track total runtime
game_start_time = time.time()

# Game state
player_position = 0
direction = 1  # 1 = right, -1 = left

# Simple counters
frames = 0
last_fps_print = time.time()

print("Game started...")

while game_running:
    frame_start = time.time()

    # ---- PROCESS INPUT (simple simulated input) ----
    # Flip direction every 30 frames (like a simple AI / input change)
    if frames % 30 == 0 and frames != 0:
        direction *= -1

    # ---- UPDATE GAME STATE ----
    player_position += direction

    # Keep player in bounds 0..10
    if player_position < 0:
        player_position = 0
        direction = 1
    elif player_position > 10:
        player_position = 10
        direction = -1

    # ---- RENDER FRAME ----
    # Simple text "render"
    print("Player position:", player_position)

    # ---- FPS CONTROL ----
    frame_time = time.time() - frame_start
    sleep_time = FRAME_TIME - frame_time
    if sleep_time > 0:
        time.sleep(sleep_time)

    # ---- FPS COUNTER (prints about once per second) ----
    frames += 1
    now = time.time()
    if now - last_fps_print >= 1.0:
        print("FPS approx:", frames)
        frames = 0
        last_fps_print = now

    # Stop after 5 seconds (termination condition)
    if time.time() - game_start_time > 5:
        game_running = False

print("Game ended.")
