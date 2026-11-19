# RubikCV

An Android app that scans a twisty puzzle with the phone camera, checks that the scan is valid, solves it, and walks you through the solution move by move.

Supported puzzles: **3x3 Rubik's Cube, 2x2, Skewb and Pyraminx**.

<p align="center">
  <img src="images/demo-3x3.gif" width="260" alt="Scanning and solving a 3x3 cube">
  &nbsp;&nbsp;&nbsp;
  <img src="images/demo-pyraminx.gif" width="260" alt="Scanning and solving a Pyraminx">
</p>

## How it works

1. **Scan.** The app tells you which side to show and how to hold the puzzle. Each side is read from the camera frame, and unclear frames (blur, reflections, bad angle) are rejected with a short hint.
2. **Check.** The scanned sides are checked for consistency. If the puzzle can't exist (for example, a colour appears too many times), the app points to the side that was probably misread so you only rescan that one.
3. **Solve.** The 3x3 is solved with Kociemba's two-phase algorithm in about 20 moves. The Skewb and Pyraminx are solved optimally.
4. **Follow along.** Each move is shown on a diagram. For the 3x3 there is also a live camera guide that recognises the side you are holding and draws the turn arrow on it.

## Screenshots

| Home | Scanning | Scan check |
|:---:|:---:|:---:|
| <img src="images/01-home.png" width="220"> | <img src="images/02-scan.png" width="220"> | <img src="images/03-check.png" width="220"> |

| Camera guide | Misread detection | Solved |
|:---:|:---:|:---:|
| <img src="images/04-guide.png" width="220"> | <img src="images/05-invalid-scan.png" width="220"> | <img src="images/06-solved.png" width="220"> |

## Tech

- Java 17, Android (Views UI), CameraX
- Own computer vision code in plain Java, with no OpenCV and no machine learning
- Own implementation of the two-phase solver for the 3x3, plus optimal solvers for the Skewb and Pyraminx
- Separate core modules for the puzzle models, validation, solvers and vision
- Unit tests for the solvers and recognition, and UI flow tests with Robolectric