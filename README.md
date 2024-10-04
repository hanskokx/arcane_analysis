This package provides lint rules for Dart and Flutter which are used by the [Arcane Framework](https://github.com/hanskokx/arcane_framework). For more information, see the [complete list of options](https://github.com/hanskokx/arcane_analysis/blob/main/lib/analysis_options.1.0.0.yaml).

**Note**: Although the linting rules differ, the package layout has taken enormous inspiration from the excellent [very_good_analysis](https://github.com/VeryGoodOpenSource/very_good_analysis) package from [Very Good Ventures](https://verygood.ventures/), which was in turn heavily inspired by [pedantic](https://github.com/dart-lang/pedantic).

## Usage

To use the linting rules, add this package as a dev dependency in your `pubspec.yaml`:

```shell
dart pub add dev:arcane_analysis
# or
flutter pub add dev:arcane_analysis
```

Then, include it in `analysis_options.yaml`:

```yaml
include: package:arcane_analysis/analysis_options.yaml
```

This will ensure you always use the latest version of the lints. If you wish to restrict the lint version, specify a version of `analysis_options.yaml` instead:

```yaml
include: package:arcane_analysis/analysis_options.1.0.0.yaml
```

## Suppressing Lints

There may be cases where specific lint rules are undesirable. Lint rules can be suppressed at the line, file, or project level.

An example use case for suppressing lint rules at the file level is suppressing the `prefer_const_constructors` in order to achieve 100% code coverage. This is due to the fact that `const` constructors are executed before the tests are run, resulting in no coverage collection.

### Line Level

To suppress a specific lint rule for a specific line of code, use an `ignore` comment directly above the line:

```dart
void doSomething() {
  // ignore: avoid_print
  print("This would produce a warning.");
}
```

### File Level

To suppress a specific lint rule of a specific file, use an `ignore_for_file` comment at the top of the file:

```dart
// ignore_for_file: avoid_print

void doSomething() {
  print("This would produce a warning.");
}
```

### Project Level

To suppress a specific lint rule for an entire project, modify `analysis_options.yaml`:

```yaml
include: package:arcane_analysis/analysis_options.yaml
linter:
  rules:
    avoid_print: false
```

## Badge

To indicate your project is using `arcane_analysis` → ![Arcane analysis Badge](https://img.shields.io/badge/style-arcane_analysis-6E35AE)

```md
[![style: arcane analysis](https://img.shields.io/badge/style-arcane_analysis-6E35AE)](https://pub.dev/packages/arcane_analysis)
```
