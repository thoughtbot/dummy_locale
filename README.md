# Dummy Locale

Dummy Locale builds a complete copy of the specified source locale at runtime.

## But Why?

> Product Manager: "We need to ensure our application is ready for
> internationalization."
>
> Developer: "Alright, I have extracted all strings to translations."
>
> Product Manager: "How can I verify this work is complete?"
>
> Developer: "Umm..."

Even if the product manager takes your assertion on faith, you've likely missed
labels generated by form builders, full error messages displayed when
re-rendering forms, and other strings that Rails defaults to English via
`humanize`. Even raising on missing translations will fail to catch these.

Dummy Locale builds a complete copy of your source locale, with each value
"translated" by bracketing it with the locale. For example, in the default
configuration, a key that translates to "Example" in the source locale will
translate to "ZZExampleZZ" in the dummy locale.

The application remains usable but allows developers and product managers to
easily see which strings may have been missed.

## Installation

Add `gem "dummy_locale"` to your Gemfile and bundle. It is recommended this be
added to development and staging environments.

## Usage

Create `config/initializers/dummy_locale.rb` like so:

```ruby
if defined?(DummyLocale)
  DummyLocale.generate(source_locale: :en, destination_locale: :zz)
end
```

Those are the default values for `source_locale` and `destination_locale`. They
can be omitted if desired.

Run `rails server`, visit your application, and switch your locale to the
`destination_locale`.

## About

Dummy Locale is maintained by [Derek Prior]
[Derek Prior]: http://prioritized.net
