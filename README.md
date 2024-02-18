# pipeline-io

Welcome to pipeline-io, a versatile open-source software solution designed to simplify data management and transformation tasks. While there are no releases available just yet, we're excited to provide you with a sneak peek into the capabilities and vision of this project.

## Project Objective:

The primary objective of pipeline-io is to empower users to effortlessly handle data from various sources and apply a wide range of data manipulation functions. Whether you need a Command-Line Interface (CLI) application or a library to integrate into your existing software, pipeline-io has you covered.

## Key Features:

- Pipeline-Based Data Processing: pipeline-io employs a pipeline-based approach, enabling users to create data processing workflows by connecting different data sources and applying a series of data transformation functions.

- Versatile Data Connections: You can seamlessly connect to multiple data sources, including MongoDB, MS SQL, RabbitMQ, and more. These connections can serve as both input and output points within your data pipeline.

- Extensive Data Manipulation Functions: pipeline-io offers a rich set of built-in functions to manipulate, transform, and enrich your data. Whether you need to clean, reshape, or aggregate data, our library provides the tools you need.

## Getting Started:

While we're still in the early stages of development, we're committed to providing detailed information and practical examples to help you understand how to use pipeline-io effectively. Stay tuned for updates as we work towards our first official release.

## Contributions and Feedback:

We believe in the power of community collaboration. pipeline-io is an open-source project, and we welcome contributions from developers, data enthusiasts, and anyone interested in improving data processing workflows. If you have ideas, suggestions, or want to get involved, please don't hesitate to reach out.

Thank you for your interest in pipeline-io. We look forward to sharing more about this project with you soon. Stay tuned for updates and dive into the world of seamless data management and transformation!

## Support me
Here's the option for you to buy me a coffee - if you like my software, if you find it useful and you can, please consider this small gesture for all the hard work I've been putting into these projects.

That would mean a lot to me!

Of course, don't feel pressured if you can't, I will continue to support and create more software.

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/kalstong)


# How to start

Run in developer mode
```
npm start -- --pipeline tests/pipeline_helloworld.json
```

# Documentation

## Pipeline structure
Pipeline is a `yaml` file with the following `nodes`:
```
connections:

variables:

callbacks:

functions:

start: []

```

As the name suggests, connection definitions are declared under the `connections` `node`. The same for variables and callbacks.

The functions are declared under the `functions` `node`.

`start` array can be used to specify witch pipeline functions are executed as soon as the pipeline are loaded and the connections established and the variables defined.

## Connections
... to be written

## Variables
### `initValue`
```
variables:
    myVar:
        initValue: ""
```
### `onSet` trigger a function or another variable
When some value are set into these variable, the variable itself invokes a function(s) by the name inside the `fn` array and pass by parameter is value.
The same happens when the `onSet` finds a `var`, in that case the variables found inside the `var` arrays will be settled with is value. Multiple `onSet` can be defined.
```
variables:
    myVar:
        initValue: ""
        - onSet:
            fn: [ "myFunc" ]
            var: [ "myOtherVariable" ]
```
### `onSet` trigger a function or another variable under a condition
In this case the functions or variables defined inside the `onSet` will be settled or invoked if the condition `variable -> operator -> value` are met.
In these case, whenever the `myVar2` value are `!==` from `someValue` the function `myFunc` will be invoked. If the myVar2 are a object, a `path: [ "inner", "object", "path" ]` can be added beside the `op` and `value`. Multiple `onSet` can be defined.

```
variables:
    myVar2:
        initValue: ""
        - onSet:
            op: "!=="
            value: "someValue"
            fn: [ "myFunc" ]
```

## Callbacks
... to be written

## Functions
... to be written
