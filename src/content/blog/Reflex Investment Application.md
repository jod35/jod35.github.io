---
title: "Reflex Investment Application"
description: "Reflex is a web framework that allows you build full-stack web applications using Pure Python. This gives a chance to people with little to know JavaScript knowledge to ship apps with Python."
pubDate: "Dec 31 2023"
---

## 1. Introduction
Reflex is a web framework that allows you build full-stack web applications using Pure Python. This gives a chance to people with little to know JavaScript knowledge to ship apps with Python.

<!-- more -->
## 2. Project Set Up
### Install Reflex
Installing Reflex is done through pip with `pip install reflex`
###  Creating a Reflex project
Creating a Reflex project can be done through the Reflex CLI. This can be accessed using the `reflex` command. 

- `reflex --help` shows all commands 
- `reflex init` helps you create a project (selecting a template)
## 3. Basic Folder Structure Explained
- `.web`  is a folder that the compiled JavaScript code (NextJS application) will reside
- `assets` static assets like CSS, images and JS are stored here
- `<the main project folder>` is where all source code for the application will be
- `.gitignore` git ignore for the project
- `requirements.txt` shows the requirements file for the project
- `rxconfig.py` is the main configuration file for your project (Will Discuss this later)
 
## 4. Basic Concepts
Inside the main project folder is the main app code. which looks something like this. 
```python
#<main-project-folder>/<project-name.py>
"""Welcome to Reflex! This file outlines the steps to create a basic app."""

import reflex as rx
from rxconfig import config

class State(rx.State): ..

"""The app state."""

def index() -> rx.Component:
	# Welcome Page (Index)
	return rx.container(
		rx.color_mode.button(position="top-right"),
		rx.vstack(
			rx.heading("Welcome to Reflex!", size="9"),
			rx.text(
			"Get started by editing ",
			rx.code(f"{config.app_name}/{config.app_name}.py"),
			size="5",
			
			),
			rx.link(
				rx.button("Check out our docs!"),
				href="https://reflex.dev/docs/getting-started/introduction/",
				is_external=True,
			),
			spacing="5",
			justify="center",
			min_height="85vh",
		),
		rx.logo(),
		
	)
  
app = rx.App()

app.add_page(index)
```

Your entire app will be created from the `app` instance created from `rx.App()`.
```python
app = rx.App()
```
Keep in mind that the we access all reflex objects (functions, classes) from the `rx` namespace that we have created by doing so.
```python
import reflex as rx
```

Creating a page is simple, we have to create a function that returns a reflex component.

```python
def index() -> rx.Component:
	...
```


We can then return some UI components using Reflex's in-built front-end components.
```python
def index() -> rx.Component:
	# Welcome Page (Index)
	return rx.container(
		rx.color_mode.button(position="top-right"),
		rx.vstack(
			rx.heading("Welcome to Reflex!", size="9"),
			rx.text(
			"Get started by editing ",
			rx.code(f"{config.app_name}/{config.app_name}.py"),
			size="5",
			
			),
			rx.link(
				rx.button("Check out our docs!"),
				href="https://reflex.dev/docs/getting-started/introduction/",
				is_external=True,
			),
			spacing="5",
			justify="center",
			min_height="85vh",
		),
		rx.logo(),
		
	)

```

Reflex UI components are built from [Radix UI](https://www.radix-ui.com/). A JavaScript UI component library. So you can just access each of them through `rx` namespace.  [Here are more](https://reflex.dev/docs/library/) UI compoenents from  Reflex. 

To register the newly created page, you will use the `add_page` method that we call from the app instead we created.

```python
# <project-name>/<project-name>.py
import reflex as rx

def index() -> rx.Component:
	# Welcome Page (Index)
	return rx.container(
		rx.color_mode.button(position="top-right"),
		rx.vstack(
			rx.heading("Welcome to Reflex!", size="9"),
			rx.text(
			"Get started by editing ",
			rx.code(f"{config.app_name}/{config.app_name}.py"),
			size="5",
			
			),
			rx.link(
				rx.button("Check out our docs!"),
				href="https://reflex.dev/docs/getting-started/introduction/",
				is_external=True,
			),
			spacing="5",
			justify="center",
			min_height="85vh",
		),
		rx.logo(),		
	)


app = rx.App()
app.add_page(index)
```

One important line is one that imports the config for the project.
```python
from rxconfig import config
```

Let us take a look at the config. Inside `rxconfig.py`
```python
import reflex as rx

config = rx.Config(
	app_name="investment_app",
	plugins=[rx.plugins.TailwindV3Plugin()],
)
```

All reflex config is done using the `rx.Config` class in here we get to provide attributes for the settings reflex expects, some of them include
- `app_name`  The name of the app
- `app_module_import`  The path to the app module
- `loglevel` The loglevel
-  `frontend_port` the frontend port
- `backend_port` the backend port
- `db_url` the URI to the database 
- `redis_url`  the Redis URI etc.

For our case, we have a `plugins` attribute, which is adding a list of plugins we want to add to the app. We have the `TailwindV3Plugin`  to allow us have support for [Tailwind CSS](https://tailwindcss.com/)

## 5. Build the Project UI

In this tutorial we shall build an investment app. a simple one. Nothing fancy. let us run the app. 
```bash
reflex run
```

This will display the welcome page below. 

![[welcome page.png]]


## Components

Components create reusable parts of your UI. Let us create a simple UI component. 

```python
#inside <project-name>.py

def investment() -> rx.Component:
	return rx.box(
		rx.heading("Basic Investment"),
		rx.text("Interest (%): 10%"),
		rx.text("Min Amount: $ 300"),
		rx.text("Maturity Period: 365 days"),
	)
```

Let us modify the code in our main page `index` to make use of our new custom component.

```python
# ... The imports

def investment() -> rx.Component:
	return rx.box(
		rx.heading("Basic Investment"),
		rx.text("Interest (%): 10%"),
		rx.text("Min Amount: $ 300"),
		rx.text("Maturity Period: 365 days"),
	)


def index() -> rx.Component:
	# Welcome Page (Index)
	return rx.container(
		investment(),
		investment()
	)

# ... the rest of the code
```

![[Screenshot from 2025-05-29 12-53-54.png]]

We can add some styling by using the style prop that takes a dictionary of CSS styles as shown below

```python
def investment() -> rx.Component:
	return rx.box(
		rx.heading("Basic Investment"),
		rx.text("Interest (%): 10%"),
		rx.text("Min Amount: $ 300"),
		rx.text("Maturity Period: 365 days"),
		style={
		}
	)
```

#### Note
My default theme is dark. That is why you see my app dark. But you can change your theme using the following set up in your app instance. 

```python
app = rx.App(
    theme=rx.theme(
		 appearance="light"
    )
)
```

This allows us to have my them changed to a light one. 