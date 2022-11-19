# Incubations

## Mustard

Simple yet powerful IoC container in ES Native Decorator implementation.

```typescript
import { Inject, Provide } from "mustard/decorators";
import { Container } from "mustard/container";

@Provide()
class Foo {
  public run() {}
}

@Provide()
class Bar {
  @Inject()
  foo: Foo;

  public sayHi() {
    console.log("Hi");
    this.foo.run();
  }
}

Container.get(Bar).sayHi();
```



## MustardCLI

IoC & Decorators based CLI App builder, with built-in devkit.

```typescript
import { CLI, BaseCommand } from "mustard-cli";
import { Command, Option } from "mustard-cli/decorators";
import { Validator } from "mustard-cli/validator";

@Command("run")
class HelloCommand extends BaseCommand {
  constructor() {
    super();
  }

  @Option()
  public dry: boolean;

  @Option([Validator.Required.isString])
  public name: boolean;

  public run(): void {
    const modeType = this.outputUtils.highlightText(
      this.dry ? "Dry" : "Active"
    );

    console.log(`Hi ${this.name}, You are in ${modeType} mode.`);

    // chaining fs api
    this.fs
      .writeFileSync("test.txt", "Hello World!")
      .appendFileSync()
      .readFileSync();
  }
}

const cli = new CLI("MustardCLI", [HelloCommand], {
  // equivalent to the version filed of nearest package.json
  version: "auto",
  // print usage information if no command is provided
  usage: true,
});

cli.init();

```



## Devfit(Not a typo!)

All-in-one development devkit, monorepo, config, file-system, ...

```typescript
```



## Strite

Vite & Strapi.

```typescript
```

