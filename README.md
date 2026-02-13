# Fps-game-loop-example
this example shows how a loop controls fps in gaming
import time

# Target FPS
TARGET_FPS = 60

# Time per frame (in seconds)
FRAME_TIME = 1 / TARGET_FPS

# Termination condition
game_running = True

# Track total runtime
game_start_time = time.time()

print("Game started...")

while game_running:
    frame_start = time.time()

    # ---- PROCESS INPUT ----
    # (Example placeholder)
    # In a real game this checks keyboard or controller
    pass

    # ---- UPDATE GAME STATE ----
    # (Example placeholder)
    # Update player position, physics, etc.
    pass

    # ---- RENDER FRAME ----
    print("Frame rendered")

    # ---- FPS CONTROL ----
    frame_time = time.time() - frame_start
    sleep_time = FRAME_TIME - frame_time

    # Only sleep if frame finished early
    if sleep_time > 0:
        time.sleep(sleep_time)

    # Stop after 5 seconds (example termination condition)
    if time.time() - game_start_time > 5:
        game_running = False

print("Game ended.")
