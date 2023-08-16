# Python Libraries for DevOps

## Tasks

1. 
    ```python

        import json

        student_records = {
            'Alice': {
                'age': 20,
                'courses': ['Math', 'Physics'],
                'grades': {'Math': 95, 'Physics': 88}
            },
            'Bob': {
                'age': 21,
                'courses': ['Chemistry', 'Biology'],
                'grades': {'Chemistry': 78, 'Biology': 92}
            },
            'Carol': {
                'age': 19,
                'courses': ['History', 'English'],
                'grades': {'History': 85, 'English': 70}
            }
        }

        # Creates a json file from dictionary within the given path
        with open("/home/prashant/90DaysOfDevOps/day15/student_records.json", "w") as json_file:
            json.dump(student_records, json_file, indent=4)

        # Simply create a json file and print the output
        # Using indent for pretty formatting
        json_data = json.dumps(student_records, indent=4)

        # Print the JSON data
        print(json_data)

    ```

2. 
    ```python

        import json

        # Read the JSON file
        with open("/home/prashant/90DaysOfDevOps/day15/services.json", "r") as json_file:
            # Convert json to dictionary
            data = json.load(json_file)

        # Extract and print service names for each cloud service provider
        cloud_providers = ["aws", "azure", "gcp"]
        for provider in cloud_providers:
            service_name = data["services"][provider]["name"]
            print(f"{provider} : {service_name}")

    ```

> Note: `json.load()` is used to load JSON data from a file-like object (such as a file handle). `json.loads()` is used to load JSON data from a JSON-formatted string. `json.dump()` is used to write Python objects (such as dictionaries or lists) as JSON data to a file-like object. `json.dumps()` is used to serialize Python objects into a JSON-formatted string.


3. 
    ```python

        import yaml
        import json

        # Read YAML data from the file
        with open("/home/prashant/90DaysOfDevOps/day15/services.yaml", "r") as yaml_file:
            # To validate a YAML file
            try:
                yaml_data = yaml.safe_load(yaml_file)
                # Convert YAML data to JSON
                json_data = json.dumps(yaml_data, indent=4)
                print(json_data)
            except yaml.YAMLError as ex:
                print(ex)

    ```