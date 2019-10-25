Repro steps:

```sh
rails _5.2.3_ new not_a_rolling_bar
cd not_a_rolling_bar
bundle add rollbar
rails generate rollbar 27d922f966e845848f564de36b99728a
rake rollbar:test
bundle add graphql
rails generate graphql:install
```
