# Flappy Bird - AI Learns to Play (Single HTML File)

## Overview

This project is a clone of the classic Flappy Bird game, implemented **entirely within a single, self-contained HTML file**. It uses only standard HTML, CSS, and vanilla JavaScript, requiring no external libraries or build steps.

The unique aspect of this version is that **you don't play it manually**. Instead, a population of AI-controlled birds attempts to learn how to play the game autonomously through a simplified Machine Learning technique called **Neuroevolution**.

## How the AI Learns (Neuroevolution)

The project employs a combination of Genetic Algorithms (GA) and Neural Networks (NN) to enable the birds to learn:

1.  **Population:** The simulation starts with a population of multiple birds (e.g., 100).
2.  **Neural Network "Brain":** Each bird possesses a simple feed-forward neural network. This network acts as its "brain" and makes the decision of *when* to flap.
    *   **Inputs:** The network receives real-time information about the current game state relative to the bird:
        *   Bird's vertical position (Y).
        *   Bird's vertical velocity.
        *   Horizontal distance to the next upcoming pipe.
        *   Vertical distance to the center of the gap in the next pipe.
        *   *(Inputs are normalized to a common range, typically 0-1, to improve network performance)*.
    *   **Output:** The network produces a single output value. If this value exceeds a specific threshold (e.g., 0.5), the bird performs a "flap" action.
3.  **Genetic Algorithm Cycle:** This is how the population improves over time:
    *   **Play & Fitness Evaluation:** All birds in the current population attempt to play the game simultaneously. They fly until they inevitably collide with the ground, ceiling, or a pipe. A bird's **fitness** is measured by how long it survived or how far it flew (its score).
    *   **Selection:** Once all birds in a generation have crashed, the algorithm identifies the bird(s) that achieved the highest fitness (score).
    *   **Reproduction & Mutation:** A new generation of birds is created based on the most successful individuals ("parents") from the previous generation:
        *   **Elitism:** The single best-performing bird's neural network ("brain") is often copied directly and unchanged into the next generation. This ensures that the best solution found so far is not lost.
        *   **Mutation:** The remaining birds in the new population are created by taking copies of the best bird's network and applying small, random modifications (**mutations**) to its internal weights and biases. This introduces genetic variation and allows the population to explore potentially better flight strategies.
    *   **Repeat:** This new generation of birds then attempts to play the game, and the cycle of playing, evaluating fitness, selecting the best, and reproducing with mutation continues indefinitely.

## Game Mechanics

The underlying simulation includes the standard Flappy Bird game mechanics:

*   Constant downward **gravity** affecting each bird.
*   A **"flap"** action providing an upward velocity boost.
*   Horizontally moving **pipes** with randomly positioned vertical gaps.
*   **Collision detection** with pipes, the ground, and the ceiling.

## Visualization

The HTML canvas visually renders the simulation:

*   All currently **alive birds** are drawn (often with varying colors for differentiation).
*   The moving **pipes** are displayed.
*   A simple **ground** graphic is shown.
*   Key **statistics** are displayed below the canvas:
    *   Current Generation number.
    *   Best Score achieved by any bird across *all* generations so far.
    *   Number of birds still active (alive) in the *current* generation.

## Technology Used

*   **HTML:** Structures the page and the `<canvas>` element.
*   **CSS:** Styles the basic page layout and canvas appearance.
*   **JavaScript (Vanilla):** Implements *all* game logic, physics simulation, neural network calculations, genetic algorithm steps, and rendering onto the canvas.
*   **No external libraries or frameworks are required.**

## How to Run

1.  Download the `flappy_ml.html` file
2.  Open this HTML file directly in a modern web browser (such as Chrome, Firefox, Edge, Safari).
3.  The simulation will start automatically.

## Expected Behavior

The simulation begins immediately upon opening the file.

*   **Initial Generations:** Birds will likely perform very poorly, flapping erratically and crashing almost instantly.
*   **Learning Over Time:** As the simulation progresses through generations (which happens automatically each time all birds crash), you should observe gradual improvements. Birds will start surviving longer, navigating gaps more consistently, and achieving higher scores.
*   **Patience Required:** Significant improvement often requires letting the simulation run through many generations (dozens, hundreds, or even thousands depending on parameters and luck).

## Purpose

This project serves as a simple, accessible demonstration of how neuroevolution principles can be applied to train AI agents to perform tasks within a simulated environment. It showcases the power of combining genetic algorithms and neural networks for learning complex behaviors, all within the constraints of a single, easily shareable, browser-runnable HTML file.
