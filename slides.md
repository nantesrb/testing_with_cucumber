# Test d'acceptation
### (ou recette)

vvv

## 😱
<img class="big" src="https://media.giphy.com/media/aK6wOUDD20N56/giphy.gif" alt="failing test gif">

vvv

> Tests qui permettent de vérifier si toutes les exigences client, décrites dans les spécifications, sont respectées.

---

# Cucumber

> Cucumber is a tool that supports Behaviour-Driven Development (BDD)

[github](https://github.com/cucumber/cucumber)

vvv

- Test sur une application en local
- Test sur une application en production (ou staging)

vvv

### Tester une `user story`

`register.feature`
```gherkin
Feature: Register
  In order to order to buy my product
  The visitors
  Should be able to register

@javascript
Scenario: Find the register page
  When  I visit "https://guillaumecabanel.github.io/app/"
    And I follow the link "I want to register!"

  Then  I should be on "https://www.meetup.com/Nantes-rb/"
```

👉 Test [this awesome app](https://guillaumecabanel.github.io/app/) !

vvv

### Est-ce magique ?

👉 live code

vvv

Non, ce n'est pas magique 😢

`register.feature`
```ruby
# Actions

When(/^I visit "([^"]+)"$/) do |url|
  visit url
end

When(/^I follow the link "([^"]+)"$/) do |link_text|
  click_link(link_text)
end

# Expectations

Then(/^I should be at "([^"]+)"$/) do |url|
  expect(current_url).to match(/#{url}/)
end
```

---

`Test d'un scenario`
```
cucumber -n "Find the register page"
```

`Rapport au format html`
```
cucumber --format html --out report.html
```

---

### Installation

👉 [vrai guide Cucumber](https://github.com/cucumber/cucumber/wiki/Install)

👉 [vrai guide Capybara](https://github.com/teamcapybara/capybara)

`Gemfile`
```ruby
gem 'rspec'
gem 'capybara'
gem 'cucumber'
```

```
bundle install
```

vvv

### 🎄

```
├── app
├── features
    ├── a_feature.feature
    ├── other_feature.feature
    ├── step_definitions
    └── support
        ├── env.rb
        └── ...

```

vvv

`features/support/env.rb`
```
require "capybara/cucumber"
require "capybara/rspec"

Capybara.default_driver = :selenium
# Capybara.default_driver = :selenium_chrome
# Capybara.default_driver =  :selenium_chrome_headless
```

vvv

Pour Ruby on Rails :
`Gemfile`
```ruby
group :test, :development do
  gem 'cucumber-rails', :require => false
  # database_cleaner is not required, but highly recommended
  gem 'database_cleaner'
end
```

```
bundle install
```

```
rails generate cucumber:install
```

---

## Avantages

- Pas de connaissance technique pour la lecture et rédaction
- Export des rapports faciles
- Peut servir de cahier des charges
- Peut servir de documentation

vvv

## Un monde parfait ?

- Résultats aléatoires sur les sites distants
- Calvaire du test sur les datepicker

---

# Merci.
# 🍻
