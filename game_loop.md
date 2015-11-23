```java
/**
 * libGDX game loop based on http://gafferongames.com/game-physics/fix-your-timestep/
 *
 */
public class GameLoop extends ApplicationAdapter {

	private long nanosPerLogicTick = 250000000; // ~ dt
	private long currentTime = System.nanoTime();

	private long accumulator;

	@Override
	public void create () {
	}

	@Override
	public void render () {
		Gdx.gl.glClearColor(1, 0, 0, 1);
		Gdx.gl.glClear(GL20.GL_COLOR_BUFFER_BIT);



		long newTime = System.nanoTime();
		long frameTime = newTime - currentTime;

		if (frameTime > 250000000) {
			frameTime = 250000000;    // Note: Avoid spiral of death
		}

		currentTime = newTime;
		accumulator += frameTime;

		while (accumulator >= nanosPerLogicTick) {

			// STORE CURRENT STATE

			// UPDATE LOGIC HERE

			accumulator -= nanosPerLogicTick;
		}


		// INTERPOLATE BETWEEN CURRENT AND STORED STATE

		// RENDER HERE
	}
}```
