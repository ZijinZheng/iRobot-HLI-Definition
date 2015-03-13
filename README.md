#iRobot High-Level Instruction Definition

OP: iRobot Open Interface Document

## Navigation

### FORWARD, BACKWARD

Move forward or backward according to the given moving distance and time duration.

	FORWARD [distance(mm)], [duration(s)]

Example

	// FORWARD 300mm in 2s
	FORWARD 300, 2

### LEFT, RIGHT

Rotate left or right according to the given angle.

	LEFT [angle(degree)]

Example

	// Left rotate 90 degree
	LEFT 90

## DRIVE

[Op, 9] Drive iRobot's wheels.

	DRIVE [velocity(mm/s)], [turn_radius(mm)]

## DEMO
[OP, 8] Play the built-in demo. Refer to .

Example: Play demo 0 to cover the floor:

	DEMO 0

## DELAY

	DELAY [duration(ms)]

## LED

[Op. 9]

	LED [LED_bits], [power_color], [power_intensity]
	
## SONG

[Op. 11] Use `SONG_DEF` to define a song and use `SONG_PLAY` to play the song you defined before.

	SONG_DEF [No],[note1],[length1],[note2],[length2]...
	SONG_PLAY [No]


## READ_SENSOR

Read sensors' data

	READ_SENSOR

## IF

IF contains `IF`, `ELSE` and `END_IF`. `ELSE` part cannot be ommited, even no sub-program is inside it. Execute `[subprogram1]` if `[condition]` is true, else execute `[subprogram2]`.

	IF [condition]
		[subprogram1]
	ELSE
		[subprogram1]
	END_IF

**subprogram**: A HLProgram.

**condition**: `[sensor], [operator], [value]`

**operator**

They are defined in `HLProgram`:

	EQUAL                 0
	NOT_EQUAL             1
	GREATER_THAN          2
	GREATER_THAN_OR_EQUAL 3
	LESS_THAN             4
	LESS_THAN_OR_EQUAL    5

Example

	// Cliff = 2, EQUAL = 0
	IF 2,0,1
		DELAY 200
	ELSE
		FORWARD 300, 2
	END_IF


## LOOP

Execute `[subprogram]` when `[condition]` is true

	LOOP [condition]
		[subprogram]
	END_LOOP

Example

	// Bump = 0, NPT_EQUAL = 1
	LOOP 0, 1, 1
		LED 10, 255, 255
		DELAY 1000
	END_LOOP


## Examples

Keep driving forward until a wall is met

	// Bump = 0, NOT_EQUAL = 1
	LOOP 0, 1, 1
		// SRAIGHT = 32768
		DRIVE 300, 32768
		DELAY 300
	END_LOOP
	DRIVE 0, 32768
