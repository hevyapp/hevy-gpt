# HevyGPT

This repo holds the configuration for [HevyGPT](https://chatgpt.com/g/g-68278fb711f881919f635175ace543f9-hevy-gym-workout-planner). Trying to improve a Custom GPT is finicky to say the least. This repo is meant to be a “master” copy of the last stable configuration. This way we always have a state to go back to if we break something while tinkering with the configs.

## Learnings

- Passing the exercise list as a file seems to break the GPTs ability to make API calls. Having the exercise list in the description fixed that.
- The API Key has to be passed as a url query parameter. ChatGPT isn’t able to insert variable values into HTTP headers.
- If the GPT is doing weird things with the API you can constrain its behaviour by modifying the OpenAPI spec. For example it was passing a superset_id of 0 for all exercises when creating a routine. To fix that I modified the spec to use type `enum: [null]`.
- It seems to perform better if there are fewer exercises to choose from. I've reduced the exercise library to just 100 exercises.

## Test Prompts

- I'd like to gain muscle and get stronger. I have access to all the typical gym equipment. Can you build me a set of 4 routines that I can do weekly? Please add a fun emoji to the title of each routine.
- How much did I lift the last time I did Bench Press? In lbs please.

## Configuration

#### Name

Hevy - Gym workout planner

#### Description

Tell me your fitness goals and available equipment, and I'll create a personalised program and upload it directly to your Hevy account.

#### Instructions

You build gym workout plans. In Hevy a workout plan is n routines in a folder.

Build the plan in the prompt with the user before you ask if they'd like it saved to Hevy.

Use these exercise templates when creating routines:

{
  "exercise_templates": [
    {
      "id": "A69FF221",
      "title": "Arnold Press (Dumbbell)"
    },
    {
      "id": "A05C064D",
      "title": "Back Extension (Machine)"
    },
    {
      "id": "79D0BB3A",
      "title": "Bench Press (Barbell)"
    },
    {
      "id": "3601968B",
      "title": "Bench Press (Dumbbell)"
    },
    {
      "id": "55E6546F",
      "title": "Bent Over Row (Barbell)"
    },
    {
      "id": "23E92538",
      "title": "Bent Over Row (Dumbbell)"
    },
    {
      "id": "A5AC6449",
      "title": "Bicep Curl (Barbell)"
    },
    {
      "id": "37FCC2BB",
      "title": "Bicep Curl (Dumbbell)"
    },
    {
      "id": "BB792A36",
      "title": "Burpee"
    },
    {
      "id": "651F844C",
      "title": "Cable Fly Crossovers"
    },
    {
      "id": "47B9DF13",
      "title": "Calf Extension (Machine)"
    },
    {
      "id": "6FCD7755",
      "title": "Chest Dip"
    },
    {
      "id": "12017185",
      "title": "Chest Fly (Dumbbell)"
    },
    {
      "id": "78683336",
      "title": "Chest Fly (Machine)"
    },
    {
      "id": "7EB3F7C3",
      "title": "Chest Press (Machine)"
    },
    {
      "id": "29083183",
      "title": "Chin Up"
    },
    {
      "id": "724CDE60",
      "title": "Concentration Curl"
    },
    {
      "id": "DCF3B31B",
      "title": "Crunch"
    },
    {
      "id": "EB43ADD4",
      "title": "Crunch (Machine)"
    },
    {
      "id": "C6272009",
      "title": "Deadlift (Barbell)"
    },
    {
      "id": "5F4E6DD3",
      "title": "Deadlift (Dumbbell)"
    },
    {
      "id": "DA0F0470",
      "title": "Decline Bench Press (Barbell)"
    },
    {
      "id": "18487FA7",
      "title": "Decline Bench Press (Dumbbell)"
    },
    {
      "id": "FAF31231",
      "title": "Decline Bench Press (Machine)"
    },
    {
      "id": "BC10A922",
      "title": "Decline Crunch"
    },
    {
      "id": "C43825EA",
      "title": "Decline Push Up"
    },
    {
      "id": "F1E57334",
      "title": "Dumbbell Row"
    },
    {
      "id": "3303376C",
      "title": "Elliptical Trainer"
    },
    {
      "id": "5046D0A9",
      "title": "Front Squat"
    },
    {
      "id": "CDA23948",
      "title": "Glute Bridge"
    },
    {
      "id": "CBA02382",
      "title": "Glute Kickback (Machine)"
    },
    {
      "id": "987234AB",
      "title": "Glute Kickback on Floor"
    },
    {
      "id": "3D0C7C75",
      "title": "Goblet Squat"
    },
    {
      "id": "4180C405",
      "title": "Good Morning (Barbell)"
    },
    {
      "id": "36E8F14E",
      "title": "Hammer Curl (Cable)"
    },
    {
      "id": "7E3BC8B6",
      "title": "Hammer Curl (Dumbbell)"
    },
    {
      "id": "08590920",
      "title": "Hanging Knee Raise"
    },
    {
      "id": "F8356514",
      "title": "Hanging Leg Raise"
    },
    {
      "id": "F4B4C6EE",
      "title": "Hip Abduction (Machine)"
    },
    {
      "id": "8BEBFED6",
      "title": "Hip Adduction (Machine)"
    },
    {
      "id": "92B8C7E1",
      "title": "Hip Thrust"
    },
    {
      "id": "D57C2EC7",
      "title": "Hip Thrust (Barbell)"
    },
    {
      "id": "68CE0B9B",
      "title": "Hip Thrust (Machine)"
    },
    {
      "id": "50DFDFAB",
      "title": "Incline Bench Press (Barbell)"
    },
    {
      "id": "07B38369",
      "title": "Incline Bench Press (Dumbbell)"
    },
    {
      "id": "D3E2AB55",
      "title": "Incline Chest Fly (Dumbbell)"
    },
    {
      "id": "FBF92739",
      "title": "Incline Chest Press (Machine)"
    },
    {
      "id": "91FAFBA3",
      "title": "Iso-Lateral Low Row"
    },
    {
      "id": "AA1EB7D8",
      "title": "Iso-Lateral Row (Machine)"
    },
    {
      "id": "991833C2",
      "title": "Jumping Jack"
    },
    {
      "id": "5CC07A1F",
      "title": "Jumping Lunge"
    },
    {
      "id": "040BA2E3",
      "title": "Jump Rope"
    },
    {
      "id": "F99C211D",
      "title": "Kettlebell Clean"
    },
    {
      "id": "4E239ED8",
      "title": "Kettlebell Curl"
    },
    {
      "id": "A127DA73",
      "title": "Kettlebell Goblet Squat"
    },
    {
      "id": "9B13BA4B",
      "title": "Kettlebell High Pull"
    },
    {
      "id": "6433CD93",
      "title": "Kettlebell Shoulder Press"
    },
    {
      "id": "89304423",
      "title": "Kettlebell Snatch"
    },
    {
      "id": "F8A0FCCA",
      "title": "Kettlebell Swing"
    },
    {
      "id": "B74A95BB",
      "title": "Kneeling Push Up"
    },
    {
      "id": "98237BA2",
      "title": "Knee Raise Parallel Bars"
    },
    {
      "id": "422B08F1",
      "title": "Lateral Raise (Dumbbell)"
    },
    {
      "id": "D5D0354D",
      "title": "Lateral Raise (Machine)"
    },
    {
      "id": "6A6C31A5",
      "title": "Lat Pulldown (Cable)"
    },
    {
      "id": "473CF5B8",
      "title": "Lat Pulldown (Machine)"
    },
    {
      "id": "C7973E0E",
      "title": "Leg Press (Machine)"
    },
    {
      "id": "0482DA98",
      "title": "Leg Raise Parallel Bars"
    },
    {
      "id": "5E1A7777",
      "title": "Lunge"
    },
    {
      "id": "B537D09F",
      "title": "Lunge (Dumbbell)"
    },
    {
      "id": "7B8D84E8",
      "title": "Overhead Press (Barbell)"
    },
    {
      "id": "6AC96645",
      "title": "Overhead Press (Dumbbell)"
    },
    {
      "id": "018ADC12",
      "title": "Pendlay Row (Barbell)"
    },
    {
      "id": "0EFE8162",
      "title": "Pike Pushup"
    },
    {
      "id": "C6C9B8A0",
      "title": "Plank"
    },
    {
      "id": "1B2B1E7C",
      "title": "Pull Up"
    },
    {
      "id": "392887AA",
      "title": "Push Up"
    },
    {
      "id": "FE389074",
      "title": "Rack Pull"
    },
    {
      "id": "2B4B7310",
      "title": "Romanian Deadlift (Barbell)"
    },
    {
      "id": "72CFFAD5",
      "title": "Romanian Deadlift (Dumbbell)"
    },
    {
      "id": "0222DB42",
      "title": "Rowing Machine"
    },
    {
      "id": "062AB91A",
      "title": "Seated Calf Raise"
    },
    {
      "id": "11A123F3",
      "title": "Seated Leg Curl (Machine)"
    },
    {
      "id": "91AF29E0",
      "title": "Seated Overhead Press (Barbell)"
    },
    {
      "id": "9930DF71",
      "title": "Seated Overhead Press (Dumbbell)"
    },
    {
      "id": "1DF4A847",
      "title": "Seated Row (Machine)"
    },
    {
      "id": "9237BAD1",
      "title": "Seated Shoulder Press (Machine)"
    },
    {
      "id": "878CD1D0",
      "title": "Shoulder Press (Dumbbell)"
    },
    {
      "id": "ABEC557F",
      "title": "Shrug (Dumbbell)"
    },
    {
      "id": "022DF610",
      "title": "Sit Up"
    },
    {
      "id": "68F8A292",
      "title": "Skullcrusher (Dumbbell)"
    },
    {
      "id": "D04AC939",
      "title": "Squat (Barbell)"
    },
    {
      "id": "9694DA61",
      "title": "Squat (Bodyweight)"
    },
    {
      "id": "06745E58",
      "title": "Standing Calf Raise"
    },
    {
      "id": "073032BB",
      "title": "Standing Military Press (Barbell)"
    },
    {
      "id": "243710DE",
      "title": "Treadmill"
    },
    {
      "id": "28BB4A95",
      "title": "Triceps Dip"
    },
    {
      "id": "21310F5F",
      "title": "Triceps Extension (Cable)"
    },
    {
      "id": "3765684D",
      "title": "Triceps Extension (Dumbbell)"
    },
    {
      "id": "6127A3AD",
      "title": "Triceps Kickback (Dumbbell)"
    },
    {
      "id": "93A552C6",
      "title": "Triceps Pushdown"
    },
    {
      "id": "94B7239B",
      "title": "Triceps Rope Pushdown"
    }
  ]
}

#### Conversation starters

- I want to bulk up this summer. I go to the gym 4 days a week, so I’d like 4 routines created to do weekly to get swole! Please add fun emoji titles to each routine and put them in a new folder. Please at least 3 sets per exercise.
- Build me 4 dumbbell only routines
- I'd like a full body routine, only bodyweight exercises

#### Capabilities

- [x] Web search
- [ ] Canvas
- [ ] 4o Image Generation
- [ ] Code Interpreter & Data Analysis

#### Action - api.hevyapp.com

#### Authentication

None

#### Schema

```
{
  "openapi": "3.1.0",
  "info": {
    "title": "Hevy API Docs",
    "description": "",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "https://hevy.com"
    }
  ],
  "paths": {
    "/api/v1/workouts": {
      "get": {
        "operationId": "get-workouts",
        "security": [
          {
            "oauth2": ["read:workouts"]
          }
        ],
        "summary": "Get a paginated list of workouts",
        "tags": [
          "Workouts"
        ],
        "parameters": [
          {
            "in": "query",
            "name": "page",
            "schema": {
              "type": "integer",
              "default": 1
            },
            "description": "Page number (Must be 1 or greater)"
          },
          {
            "in": "query",
            "name": "pageSize",
            "schema": {
              "type": "integer",
              "default": 5
            },
            "description": "Number of items on the requested page (Max 10)"
          }
        ],
        "responses": {
          "200": {
            "description": "A paginated list of workouts",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "page": {
                      "type": "integer",
                      "example": 1,
                      "description": "Current page number"
                    },
                    "page_count": {
                      "type": "integer",
                      "example": 5,
                      "description": "Total number of pages"
                    },
                    "workouts": {
                      "type": "array",
                      "items": {
                        "$ref": "#/components/schemas/Workout"
                      }
                    }
                  }
                }
              }
            }
          },
          "400": {
            "description": "Invalid page size"
          }
        }
      },
    },
    "/api/v1/routines": {
      "get": {
        "operationId": "get-routines",
        "security": [
          {
            "oauth2": ["read:routines"]
          }
        ],
        "summary": "Get a paginated list of routines",
        "tags": [
          "Routines"
        ],
        "parameters": [
          {
            "in": "query",
            "name": "page",
            "schema": {
              "type": "integer",
              "default": 1
            },
            "description": "Page number (Must be 1 or greater)"
          },
          {
            "in": "query",
            "name": "pageSize",
            "schema": {
              "type": "integer",
              "default": 5
            },
            "description": "Number of items on the requested page (Max 10)"
          }
        ],
        "responses": {
          "200": {
            "description": "A paginated list of routines",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "page": {
                      "type": "integer",
                      "example": 1,
                      "description": "Current page number"
                    },
                    "page_count": {
                      "type": "integer",
                      "example": 5,
                      "description": "Total number of pages"
                    },
                    "routines": {
                      "type": "array",
                      "items": {
                        "$ref": "#/components/schemas/Routine"
                      }
                    }
                  }
                }
              }
            }
          },
          "400": {
            "description": "Invalid page size"
          }
        }
      },
      "post": {
        "operationId": "post-routine",
        "security": [
          {
            "oauth2": ["write:routines"]
          }
        ],
        "summary": "Create a new routine",
        "tags": [
          "Routines"
        ],
        "parameters": [],
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/PostRoutinesRequestBody"
              }
            }
          }
        },
        "responses": {
          "201": {
            "description": "The routine was successfully created",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/Routine"
                }
              }
            }
          },
          "400": {
            "description": "Invalid request body",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "error": {
                      "type": "string",
                      "description": "Error message"
                    }
                  }
                }
              }
            }
          },
          "403": {
            "description": "Routine limit exceeded",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "error": {
                      "type": "string",
                      "description": "Error message"
                    }
                  }
                }
              }
            }
          }
        }
      }
    },
    "/api/v1/routines/{routineId}": {
      "get": {
        "operationId": "get-routine",
        "security": [
          {
            "oauth2": ["read:routines"]
          }
        ],
        "summary": "Get a routine by its Id",
        "tags": [
          "Routines"
        ],
        "parameters": [
          {
            "in": "path",
            "name": "routineId",
            "description": "The id of the routine",
            "required": true
          }
        ],
        "responses": {
          "200": {
            "description": "The routine with the provided id",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "routine": {
                      "$ref": "#/components/schemas/Routine"
                    }
                  }
                }
              }
            }
          },
          "400": {
            "description": "Invalid request body",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "error": {
                      "type": "string",
                      "description": "Error message"
                    }
                  }
                }
              }
            }
          }
        }
      },
    },
    "/api/v1/routine_folders": {
      "get": {
        "summary": "Get a paginated list of routine folders available on the account.",
        "tags": [
          "RoutineFolders"
        ],
        "operationId": "get-routine-folders",
        "security": [
          {
            "oauth2": ["read:routine_folders"]
          }
        ],
        "parameters": [
          {
            "in": "query",
            "name": "page",
            "schema": {
              "type": "integer",
              "default": 1
            },
            "description": "Page number (Must be 1 or greater)"
          },
          {
            "in": "query",
            "name": "pageSize",
            "schema": {
              "type": "integer",
              "default": 5
            },
            "description": "Number of items on the requested page (Max 10)"
          }
        ],
        "responses": {
          "200": {
            "description": "A paginated list of routine folders",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "page": {
                      "type": "integer",
                      "default": 1,
                      "description": "Current page number"
                    },
                    "page_count": {
                      "type": "integer",
                      "default": 5,
                      "description": "Total number of pages"
                    },
                    "routine_folders": {
                      "type": "array",
                      "items": {
                        "$ref": "#/components/schemas/RoutineFolder"
                      }
                    }
                  }
                }
              }
            }
          },
          "400": {
            "description": "Invalid page size"
          }
        }
      },
      "post": {
        "summary": "Create a new routine folder. The folder will be created at index 0, and all other folders will have their indexes incremented.",
        "tags": [
          "RoutineFolders"
        ],
        "operationId": "post-routine-folder",
        "security": [
          {
            "oauth2": ["write:routine_folders"]
          }
        ],
        "parameters": [],
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/PostRoutineFolderRequestBody"
              }
            }
          }
        },
        "responses": {
          "201": {
            "description": "The routine folder was successfully created",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/RoutineFolder"
                }
              }
            }
          },
          "400": {
            "description": "Invalid request body",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "error": {
                      "type": "string",
                      "description": "Error message"
                    }
                  }
                }
              }
            }
          }
        }
      }
    },
    "/api/v1/routine_folders/{folderId}": {
      "get": {
        "operationId": "get-folder",
        "security": [
          {
            "oauth2": ["read:routine_folders"]
          }
        ],
        "tags": [
          "RoutineFolders"
        ],
        "summary": "Get a single routine folder by id.",
        "parameters": [
          {
            "name": "folderId",
            "in": "path",
            "description": "The id of the routine folder",
            "required": true
          }
        ],
        "responses": {
          "200": {
            "description": "Success",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/RoutineFolder"
                }
              }
            }
          },
          "404": {
            "description": "Routine folder not found"
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "PostWorkoutsRequestSet": {
        "type": "object",
        "properties": {
          "type": {
            "type": "string",
            "description": "The type of the set.",
            "enum": [
              "warmup",
              "normal",
              "failure",
              "dropset"
            ],
            "example": "normal"
          },
          "weight_kg": {
            "type": "number",
            "nullable": true,
            "description": "The weight in kilograms.",
            "example": 100
          },
          "reps": {
            "type": "integer",
            "nullable": true,
            "description": "The number of repetitions.",
            "example": 10
          },
          "distance_meters": {
            "type": "integer",
            "nullable": true,
            "description": "The distance in meters.",
            "example": null
          },
          "duration_seconds": {
            "type": "integer",
            "nullable": true,
            "description": "The duration in seconds.",
            "example": null
          },
          "custom_metric": {
            "type": "number",
            "nullable": true,
            "description": "A custom metric for the set. Currently used for steps and floors.",
            "example": null
          },
          "rpe": {
            "type": "number",
            "nullable": true,
            "description": "The Rating of Perceived Exertion (RPE).",
            "enum": [
              6,
              7,
              7.5,
              8,
              8.5,
              9,
              9.5,
              10
            ],
            "example": null
          }
        }
      },
      "PostWorkoutsRequestExercise": {
        "type": "object",
        "properties": {
          "exercise_template_id": {
            "type": "string",
            "description": "The ID of the exercise template.",
            "example": "D04AC939"
          },
          "superset_id": {
            "type": "integer",
            "nullable": true,
            "description": "The ID of the superset.",
            "example": null
          },
          "notes": {
            "type": "string",
            "nullable": true,
            "description": "Additional notes for the exercise.",
            "example": "Felt good today. Form was on point."
          },
          "sets": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/PostWorkoutsRequestSet"
            }
          }
        }
      },
      "PostWorkoutsRequestBody": {
        "type": "object",
        "properties": {
          "workout": {
            "type": "object",
            "properties": {
              "title": {
                "type": "string",
                "description": "The title of the workout.",
                "example": "Friday Leg Day 🔥"
              },
              "description": {
                "type": "string",
                "nullable": true,
                "description": "A description for the workout workout.",
                "example": "Medium intensity leg day focusing on quads."
              },
              "start_time": {
                "type": "string",
                "description": "The time the workout started.",
                "example": "2024-08-14T12:00:00Z"
              },
              "end_time": {
                "type": "string",
                "description": "The time the workout ended.",
                "example": "2024-08-14T12:30:00Z"
              },
              "is_private": {
                "type": "boolean",
                "description": "A boolean indicating if the workout is private.",
                "example": false
              },
              "exercises": {
                "type": "array",
                "items": {
                  "$ref": "#/components/schemas/PostWorkoutsRequestExercise"
                }
              }
            }
          }
        }
      },
      "PostRoutinesRequestSet": {
        "type": "object",
        "properties": {
          "type": {
            "type": "string",
            "description": "The type of the set.",
            "enum": [
              "warmup",
              "normal",
              "failure",
              "dropset"
            ],
            "example": "normal"
          },
          "weight_kg": {
            "type": "number",
            "nullable": true,
            "description": "The weight in kilograms.",
            "example": 100
          },
          "reps": {
            "type": "integer",
            "nullable": true,
            "description": "The number of repetitions.",
            "example": 10
          },
          "distance_meters": {
            "type": "integer",
            "nullable": true,
            "description": "The distance in meters.",
            "example": null
          },
          "duration_seconds": {
            "type": "integer",
            "nullable": true,
            "description": "The duration in seconds.",
            "example": null
          },
          "custom_metric": {
            "type": "number",
            "nullable": true,
            "description": "A custom metric for the set. Currently used for steps and floors.",
            "example": null
          }
        }
      },
      "PostRoutinesRequestExercise": {
        "type": "object",
        "properties": {
          "exercise_template_id": {
            "type": "string",
            "description": "The ID of the exercise template.",
            "example": "D04AC939"
          },
          "superset_id": {
            "enum": [null],
            "description": "The ID of the superset.",
            "example": null
          },
          "rest_seconds": {
            "type": "integer",
            "nullable": true,
            "description": "The rest time in seconds.",
            "example": 90
          },
          "notes": {
            "type": "string",
            "nullable": false,
            "description": "Additional notes for the exercise.",
            "example": "Stay slow and controlled."
          },
          "sets": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/PostRoutinesRequestSet"
            }
          }
        }
      },
      "PostRoutinesRequestBody": {
        "type": "object",
        "properties": {
          "routine": {
            "type": "object",
            "properties": {
              "title": {
                "type": "string",
                "description": "The title of the routine.",
                "example": "April Leg Day 🔥"
              },
              "folder_id": {
                "enum": [null],
                 "description": "The folder id the routine should be added to. Only null is accepted to insert the routine into default \"My Routines\" folder",
                "example": null
              },
              "notes": {
                "type": "string",
                "description": "Additional notes for the routine.",
                "example": "Focus on form over weight. Remember to stretch."
              },
              "exercises": {
                "type": "array",
                "items": {
                  "$ref": "#/components/schemas/PostRoutinesRequestExercise"
                }
              }
            }
          }
        }
      },
      "PutRoutinesRequestSet": {
        "type": "object",
        "properties": {
          "type": {
            "type": "string",
            "description": "The type of the set.",
            "enum": [
              "warmup",
              "normal",
              "failure",
              "dropset"
            ],
            "example": "normal"
          },
          "weight_kg": {
            "type": "number",
            "nullable": true,
            "description": "The weight in kilograms.",
            "example": 100
          },
          "reps": {
            "type": "integer",
            "nullable": true,
            "description": "The number of repetitions.",
            "example": 10
          },
          "distance_meters": {
            "type": "integer",
            "nullable": true,
            "description": "The distance in meters.",
            "example": null
          },
          "duration_seconds": {
            "type": "integer",
            "nullable": true,
            "description": "The duration in seconds.",
            "example": null
          },
          "custom_metric": {
            "type": "number",
            "nullable": true,
            "description": "A custom metric for the set. Currently used for steps and floors.",
            "example": null
          }
        }
      },
      "PutRoutinesRequestExercise": {
        "type": "object",
        "properties": {
          "exercise_template_id": {
            "type": "string",
            "description": "The ID of the exercise template.",
            "example": "D04AC939"
          },
          "superset_id": {
            "type": "integer",
            "nullable": true,
            "description": "The ID of the superset.",
            "example": null
          },
          "rest_seconds": {
            "type": "integer",
            "nullable": true,
            "description": "The rest time in seconds.",
            "example": 90
          },
          "notes": {
            "type": "string",
            "nullable": true,
            "description": "Additional notes for the exercise.",
            "example": "Stay slow and controlled."
          },
          "sets": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/PutRoutinesRequestSet"
            }
          }
        }
      },
      "PutRoutinesRequestBody": {
        "type": "object",
        "properties": {
          "routine": {
            "type": "object",
            "properties": {
              "title": {
                "type": "string",
                "description": "The title of the routine.",
                "example": "April Leg Day 🔥"
              },
              "notes": {
                "type": "string",
                "nullable": true,
                "description": "Additional notes for the routine.",
                "example": "Focus on form over weight. Remember to stretch."
              },
              "exercises": {
                "type": "array",
                "items": {
                  "$ref": "#/components/schemas/PutRoutinesRequestExercise"
                }
              }
            }
          }
        }
      },
      "PostRoutineFolderRequestBody": {
        "type": "object",
        "properties": {
          "routine_folder": {
            "type": "object",
            "properties": {
              "title": {
                "type": "string",
                "description": "The title of the routine folder.",
                "example": "Push Pull 🏋️‍♂️"
              }
            }
          }
        }
      },
      "ExerciseTemplate": {
        "type": "object",
        "properties": {
          "id": {
            "type": "string",
            "description": "The exercise template ID.",
            "example": "b459cba5-cd6d-463c-abd6-54f8eafcadcb"
          },
          "title": {
            "type": "string",
            "description": "The exercise title.",
            "example": "Bench Press (Barbell)"
          },
          "type": {
            "type": "string",
            "description": "The exercise type.",
            "example": "weight_reps"
          },
          "primary_muscle_group": {
            "type": "string",
            "description": "The primary muscle group of the exercise.",
            "example": "weight_reps"
          },
          "secondary_muscle_groups": {
            "type": "array",
            "description": "The secondary muscle groups of the exercise.",
            "items": {
              "type": "string"
            }
          },
          "is_custom": {
            "type": "boolean",
            "description": "A boolean indicating whether the exercise is a custom exercise.",
            "example": false
          }
        }
      },
      "RoutineFolder": {
        "type": "object",
        "properties": {
          "id": {
            "type": "number",
            "description": "The routine folder ID.",
            "example": 42
          },
          "index": {
            "type": "number",
            "description": "The routine folder index. Describes the order of the folder in the list.",
            "example": 1
          },
          "title": {
            "type": "string",
            "description": "The routine folder title.",
            "example": "Push Pull 🏋️‍♂️"
          },
          "updated_at": {
            "type": "string",
            "description": "ISO 8601 timestamp of when the folder was last updated.",
            "example": "2021-09-14T12:00:00Z"
          },
          "created_at": {
            "type": "string",
            "description": "ISO 8601 timestamp of when the folder was created.",
            "example": "2021-09-14T12:00:00Z"
          }
        }
      },
      "Routine": {
        "type": "object",
        "properties": {
          "id": {
            "type": "string",
            "description": "The routine ID.",
            "example": "b459cba5-cd6d-463c-abd6-54f8eafcadcb"
          },
          "title": {
            "type": "string",
            "description": "The routine title.",
            "example": "Upper Body 💪"
          },
          "folder_id": {
            "type": "number",
            "nullable": true,
            "description": "The routine folder ID.",
            "example": 42
          },
          "updated_at": {
            "type": "string",
            "description": "ISO 8601 timestamp of when the routine was last updated.",
            "example": "2021-09-14T12:00:00Z"
          },
          "created_at": {
            "type": "string",
            "description": "ISO 8601 timestamp of when the routine was created.",
            "example": "2021-09-14T12:00:00Z"
          },
          "exercises": {
            "type": "array",
            "items": {
              "type": "object",
              "properties": {
                "index": {
                  "type": "number",
                  "description": "Index indicating the order of the exercise in the routine.",
                  "example": 0
                },
                "title": {
                  "type": "string",
                  "description": "Title of the exercise",
                  "example": "Bench Press (Barbell)"
                },
                "rest_seconds": {
                  "type": "string",
                  "description": "The rest time in seconds between sets of the exercise",
                  "example": 60
                },
                "notes": {
                  "type": "string",
                  "description": "Routine notes on the exercise",
                  "example": "Focus on form. Go down to 90 degrees."
                },
                "exercise_template_id": {
                  "type": "string",
                  "description": "The id of the exercise template. This can be used to fetch the exercise template.",
                  "example": "05293BCA"
                },
                "supersets_id": {
                  "type": "number",
                  "nullable": true,
                  "description": "The id of the superset that the exercise belongs to. A value of null indicates the exercise is not part of a superset.",
                  "example": 0
                },
                "sets": {
                  "type": "array",
                  "items": {
                    "type": "object",
                    "properties": {
                      "index": {
                        "type": "number",
                        "description": "Index indicating the order of the set in the routine.",
                        "example": 0
                      },
                      "type": {
                        "type": "string",
                        "description": "The type of set. This can be one of 'normal', 'warmup', 'dropset', 'failure'",
                        "example": "normal"
                      },
                      "weight_kg": {
                        "type": "number",
                        "nullable": true,
                        "description": "Weight lifted in kilograms.",
                        "example": 100
                      },
                      "reps": {
                        "type": "number",
                        "nullable": true,
                        "description": "Number of reps logged for the set",
                        "example": 10
                      },
                      "distance_meters": {
                        "type": "number",
                        "nullable": true,
                        "description": "Number of meters logged for the set",
                        "example": null
                      },
                      "duration_seconds": {
                        "type": "number",
                        "nullable": true,
                        "description": "Number of seconds logged for the set",
                        "example": null
                      },
                      "rpe": {
                        "type": "number",
                        "nullable": true,
                        "description": "RPE (Relative perceived exertion) value logged for the set",
                        "example": 9.5
                      },
                      "custom_metric": {
                        "type": "number",
                        "nullable": true,
                        "description": "Custom metric logged for the set (Currently only used to log floors or steps for stair machine exercises)",
                        "example": 50
                      }
                    }
                  }
                }
              }
            }
          }
        }
      },
      "Workout": {
        "type": "object",
        "properties": {
          "id": {
            "type": "string",
            "description": "The workout ID.",
            "example": "b459cba5-cd6d-463c-abd6-54f8eafcadcb"
          },
          "title": {
            "type": "string",
            "description": "The workout title.",
            "example": "Morning Workout 💪"
          },
          "description": {
            "type": "string",
            "description": "The workout description.",
            "example": "Pushed myself to the limit today!"
          },
          "start_time": {
            "type": "number",
            "description": "ISO 8601 timestamp of when the workout was recorded to have started.",
            "example": "2021-09-14T12:00:00Z"
          },
          "end_time": {
            "type": "number",
            "description": "ISO 8601 timestamp of when the workout was recorded to have ended.",
            "example": "2021-09-14T12:00:00Z"
          },
          "updated_at": {
            "type": "string",
            "description": "ISO 8601 timestamp of when the workout was last updated.",
            "example": "2021-09-14T12:00:00Z"
          },
          "created_at": {
            "type": "string",
            "description": "ISO 8601 timestamp of when the workout was created.",
            "example": "2021-09-14T12:00:00Z"
          },
          "exercises": {
            "type": "array",
            "items": {
              "type": "object",
              "properties": {
                "index": {
                  "type": "number",
                  "description": "Index indicating the order of the exercise in the workout.",
                  "example": 0
                },
                "title": {
                  "type": "string",
                  "description": "Title of the exercise",
                  "example": "Bench Press (Barbell)"
                },
                "notes": {
                  "type": "string",
                  "description": "Notes on the exercise",
                  "example": "Paid closer attention to form today. Felt great!"
                },
                "exercise_template_id": {
                  "type": "string",
                  "description": "The id of the exercise template. This can be used to fetch the exercise template.",
                  "example": "05293BCA"
                },
                "supersets_id": {
                  "type": "number",
                  "nullable": true,
                  "description": "The id of the superset that the exercise belongs to. A value of null indicates the exercise is not part of a superset.",
                  "example": 0
                },
                "sets": {
                  "type": "array",
                  "items": {
                    "type": "object",
                    "properties": {
                      "index": {
                        "type": "number",
                        "description": "Index indicating the order of the set in the workout.",
                        "example": 0
                      },
                      "type": {
                        "type": "string",
                        "description": "The type of set. This can be one of 'normal', 'warmup', 'dropset', 'failure'",
                        "example": "normal"
                      },
                      "weight_kg": {
                        "type": "number",
                        "nullable": true,
                        "description": "Weight lifted in kilograms.",
                        "example": 100
                      },
                      "reps": {
                        "type": "number",
                        "nullable": true,
                        "description": "Number of reps logged for the set",
                        "example": 10
                      },
                      "distance_meters": {
                        "type": "number",
                        "nullable": true,
                        "description": "Number of meters logged for the set",
                        "example": null
                      },
                      "duration_seconds": {
                        "type": "number",
                        "nullable": true,
                        "description": "Number of seconds logged for the set",
                        "example": null
                      },
                      "rpe": {
                        "type": "number",
                        "nullable": true,
                        "description": "RPE (Relative perceived exertion) value logged for the set",
                        "example": 9.5
                      },
                      "custom_metric": {
                        "type": "number",
                        "nullable": true,
                        "description": "Custom metric logged for the set (Currently only used to log floors or steps for stair machine exercises)",
                        "example": 50
                      }
                    }
                  }
                }
              }
            }
          }
        }
      },
      "UpdatedWorkout": {
        "type": "object",
        "required": [
          "type",
          "workout"
        ],
        "properties": {
          "type": {
            "type": "string",
            "description": "Indicates the type of the event (updated)",
            "example": "updated"
          },
          "workout": {
            "$ref": "#/components/schemas/Workout"
          }
        }
      },
      "DeletedWorkout": {
        "type": "object",
        "required": [
          "type",
          "id"
        ],
        "properties": {
          "type": {
            "type": "string",
            "description": "Indicates the type of the event (deleted)",
            "example": "deleted"
          },
          "id": {
            "type": "string",
            "description": "The unique identifier of the deleted workout",
            "example": "efe6801c-4aee-4959-bcdd-fca3f272821b"
          },
          "deleted_at": {
            "type": "string",
            "description": "A date string indicating when the workout was deleted",
            "example": "2021-09-13T12:00:00Z"
          }
        }
      },
      "PaginatedWorkoutEvents": {
        "type": "object",
        "required": [
          "page",
          "page_count",
          "events"
        ],
        "properties": {
          "page": {
            "type": "integer",
            "description": "The current page number",
            "example": 1
          },
          "page_count": {
            "type": "integer",
            "description": "The total number of pages available",
            "example": 5
          },
          "events": {
            "type": "array",
            "items": {
              "oneOf": [
                {
                  "$ref": "#/components/schemas/UpdatedWorkout"
                },
                {
                  "$ref": "#/components/schemas/DeletedWorkout"
                }
              ]
            },
            "description": "An array of workout events (either updated or deleted)"
          }
        }
      }
    }
  },
  "tags": []
}
```
