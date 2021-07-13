---
tags: 
---
Acceptance tests help ensure that applications we develop are deployed with minimal bugs. Manual acceptance testing is extremely valuable, but it can also be tedious and time-consuming. At DF, we've applied the automation End2End testing for our development process. In End2End test, we can open the web page, navigate on the web like a real user.
In elixir project, we can do the same thing with Hound(https://github.com/HashNuke/hound) and a WebDriver.

The WebDriver is an interface to automate browsers. We can use WebDriver implementation to build an automated test suite against a real browser.

Hound is an Elixir library to write WebDriver. Writing End2End test with Hound is very similar to writing a normal ExUnit test. An advantage to writing automation tests is the same code base.

**Common Web Drivers**
https://github.com/HashNuke/hound/wiki/Starting-a-webdriver-server
Selenium:
https://selenium-release.storage.googleapis.com/index.html
`brew install selenium-server-standalone`

ChromeDriver server:
https://chromedriver.chromium.org
`brew install --cask chromedriver`

Run command:
`chromedriver`

PhantomJS web driver
`brew cask install phantomjs`

Run command:
`phantomjs --wd`

**Configure Hound**
Add dependency to `mix.exs`:
{:hound, "~> 1.0"}

Follow the setup step in https://hexdocs.pm/phoenix_ecto/Phoenix.Ecto.SQL.Sandbox.html:
- add the plug to `Endpoint`
- update the config/test.exs to run real server when execute test cases
- add the hound config in config/test.exs. `config :hound, driver: "chrome_driver", browser: "chrome_headless"`. We can update the config for other driver and browser config.
- Update `test/test_helper.ex`. We must start :hound application before run the unit test. `Application.ensure_all_started(:hound)`

---

#### Citations