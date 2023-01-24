# VisionAI Scenarios

This repo consists of all the scenarios supported by the [Vision AI Toolkit](https://github.com/visionify/visionai). Main file is `scenarios.json` which is one large JSON file with all scenarios, categories, tags etc.

TODO: Later we would like to add some automation in terms of easily being able to add scenarios from our model experiements folder.

## Schema

The JSON file is organized as an array of scenarios. Each scenario can have all the details related to it, including name, category, tags, model_file locations, training & accuracy details, versions etc. This file lists all publicly available scenarios. Each scenario has the schema:

```json
{
    "id": "5991c1bb-be6a-4f60-99a2-3db1973c96ad",
    "name": "smoke-and-fire-detection",
    "overview": "Detect early signs of sparks, smoke or fire. This model would give real-time events when a smoke, fire, sparks are detected. It is trained with 240032 images, out of which 183453 images were from outdoors environment, and remaining images were from indoor environment. There is a good balance between day and night pictures (44-56%)",
    "docs": "https://docs.visionify.ai/scenarios/smoke-and-fire-detection.md",
    "image": "https://scenariosblob.blob.core.windows.net/scenarios-ppe-detection-description.jpg",
    "thumbnail": "https://scenariosblob.blob.core.windows.net/scenarios-ppe-detection-description-200x200.jpg",
    "metrics": {
        "accuracy": 98.2,
        "recall": 95.2,
        "f1": 95,
        "datasetSize": 240032
    },
    "model_url": "https://workplaceos.blob.core.windows.net/models/smoke-and-fire-detection/smoke-and-fire-detection-0.0.1.pt",
    "version": "0.0.1",
    "model_hash": "895c9c3205f6744b6c63564fff680ff7",
    "tags":[
        "Smoke",
        "Fire",
        "Sparks",
        "Embers",
        "Early Fire Signature",
        "Hazard warning"
    ],
    "categories": [
        "Personnel health",
        "Hazard warning"
    ],
    "events": [
        "Smoke Detected",
        "Fire Detected"
    ],
    "configuration": [
        {
            "name": "focus_area",
            "type": "region_of_interest",
            "required": false,
            "default": [0, 0, 1, 1]
        }
    ]
}
```


## Why a giant JSON file?

We thought about controlling this information through a DB/redis approach, but the problem was a good version control availability. With a JSON file, the size can increase and make it unreadable - but it would provide much better version control. Later we plan to add to add more tools that would make it easier to get just individual scenarios, scenarios by categories etc. All of these would be auto-generated files based on a single-source-of-truth.