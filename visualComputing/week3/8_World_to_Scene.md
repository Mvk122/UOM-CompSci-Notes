* A mapping from the world's coordinates to screen coordinates is needed to specify what needs to be seen and where it should be shown.
* This involves translating the window to (0,0), scaling it to be the same shape as the viewport and then shifting it to the viewport position.
* This is also where clipping parts of primitives outside the window occurs.