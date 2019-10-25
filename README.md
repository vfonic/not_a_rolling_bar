# Repro steps

## Setup

Clone this repo or:

```sh
rails _5.2.3_ new not_a_rolling_bar
cd not_a_rolling_bar
bundle add rollbar
rails generate rollbar 27d922f966e845848f564de36b99728a
rake rollbar:test
bundle add graphql
rails generate graphql:install
```

## Making an error

After running grapql install generator, replace `app/graphql/types/query_type.rb` code with this:

```rb
module Types
  class QueryType < Types::BaseObject
    # Add root-level fields here.
    # They will be entry points for queries on your schema.

    # TODO: remove me
    field :test_field, [String], null: false,
      description: "An example field added by the generator"
    def test_field
      String
    end
  end
end
```

Run rails server:

```sh
rails server
```

Visit: [http://localhost:3000/graphiql](http://localhost:3000/graphiql)

Type in the following query:

```graphql
{
  testField
}
```

Press the play button.
