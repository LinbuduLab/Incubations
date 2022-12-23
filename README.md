# Incubations

## ES-Decorator-Utils

Decorator based function utilities in ES Native Decorator implementation.

```typescript
import { Memo, Profile, Once } from "es-decorator-utils";

class Utils {
  @Once()
  InitializedOnceOnly() {}
  
  @Memo()
  Memorized() {}
  
  @Profile()
  FetchWithProfile() {}
}
```

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
#!/usr/bin/env node

import { MustardFactory } from "mustard-cli";
import {
  Command,
  RootCommand,
  Option,
  VariadicOption,
  App,
} from "mustard-cli/Decorators";
import { Validator } from "mustard-cli/Validator";
import { CommandStruct, MustardApp } from "mustard-cli/ComanndLine";

@RootCommand()
class RootCommandHandle implements CommandStruct {
  @Option("d")
  public msg = "default value of msg";

  public run(): void {
    console.log("Root Command! ", this.msg);
  }
}

@Command("update", "u", "update project dependencies")
class UpdateCommand implements CommandStruct {
  @Option("depth", "depth of packages to update", Validator.Number().Gte(1))
  public depth = 10;

  @Option(Validator.Boolean())
  public dry = false;

  @Option("all")
  public applyAll: boolean;

  @VariadicOption()
  public packages: string[];

  public run(): void {
    console.warn("DryRun Mode: ", this.dry);
    console.info("Execution Depth", this.depth);
    console.info("Specified Packages", this.packages);
  }
}

@App({
  name: "LinbuduLab CLI",
  commands: [RootCommandHandle, UpdateCommand],
  configurations: {
    enableVersion: require("./package.json").version,
  },
})
class Project implements MustardApp {
  onStart() {}

  onComplete() {}
}

MustardFactory.init(Project).start();
```



## Devfit(Not a typo!)

All-in-one development devkit, monorepo, config, file-system, ...

```typescript
```



## Strite

Vite & Strapi.

```typescript
```

