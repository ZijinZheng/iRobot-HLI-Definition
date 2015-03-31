#iRobot High-Level Instruction Definition

OP: iRobot Open Interface Document

Obsolete: The instruction cannot be generated from GUI and exists only for backward compatibility.

## Navigation

### MOVE

Move forward or backward according to the given moving distance and time duration.

	MOVE [distance(mm)], [duration(s)]

**distance**: The distance to move in millimeter. Positive value means forward and negative value means backward.

**duration**: The time duration in second.

Example

	// MOVE 300mm in 2s
	MOVE 300, 2

### ROTATE

Rotate left or right according to the given angle.

	ROTATE [angle(degree)]

**angle**: The angle to rotate in degree. Positive value means counterclockwise and negative value means clockwise.

Example

	// Left rotate 90 degree
	ROTATE 90

## DRIVE

[Op, 9] Drive iRobot's wheels.

	DRIVE [velocity(mm/s)], [turn_radius(mm)]

## DEMO

[OP, 8] Play the built-in demo.

Example: Play demo 0 to cover the floor:

	DEMO 0

## DELAY

	DELAY [duration(ms)]

**duration**: The time to delay in millisecond.

## LED

[Op. 9]

	LED [LED_bits], [power_color], [power_intensity]

## SONG

[Op. 11] Plays a song.

	SONG [note1],[length1],[note2],[length2]...

### SONG\_DEF, SONG\_PLAY (Obsolete)

[Op. 11] Define and play a song.

	SONG_DEF [No],[note1],[length1],[note2],[length2]...
	SONG_PLAY [No]

**No**: The number of the song. `SONG_PLAY` plays the song defined in `SONG_DEF` with `No`.


## READ_SENSOR (Obsolete)

Read sensors' data. The funtion of this instruction is integrated to the condition evaluation of IF and LOOP.

	READ_SENSOR

## IF

IF contains `IF`, `ELSE` and `END_IF`. `ELSE` part cannot be ommited, even no sub-program is inside it. Execute `[subprogram1]` if `[condition]` is true, else execute `[subprogram2]`.

	IF [condition]
		[subprogram1]
	ELSE
		[subprogram1]
	END_IF

**subprogram**: A HLProgram

**condition**: `[sensor], [operator], [value]`

**operator**: They are defined in `HLProgram` as follows

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

Keep driving forward until a wall is met.

	// Wall = 1, NOT_EQUAL = 1
	LOOP 1, 1, 1
		// SRAIGHT = 32768
		DRIVE 300, 32768
		DELAY 300
	END_LOOP
	DRIVE 0, 32768
