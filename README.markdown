# Template

This is a template project to be used on new contract projects. You can generate a new project using
this template with [pi](https://github.com/vmchale/project-init).

Install pi:

```
rustup run nightly cargo install project_init
```

Create a new project:

```
pi git parity-contracts/template project-name
```

The generator will ask you for your name and email but these will be ignored when generating the project.

## Code style

The code style should follow the official [Solidity style
guide](http://solidity.readthedocs.io/en/v0.4.21/style-guide.html) and is mostly enforced by the
Solium linter (`yarn lint`).

### Function declaration

Function declaration style isn't completely enforced by the linter. Function modifiers should be
declared each in their own line. Visibility modifiers (and `view`/`pure`/`payable`) should come
before any custom modifiers.

Yes:

```solidity
function kill()
    public
    payable
    onlyowner
{
    selfdestruct(owner);
}
```

No:

```solidity
function kill() public payable onlyowner {
    selfdestruct(owner);
}
```

No:

```solidity
function kill()
    onlyowner
    payable
    public
{
    selfdestruct(owner);
}
```

### Order of declarations

Order of declarations is also not enforced by the linter. Declarations should be grouped
and ordered:

- Types
- Events
- State variables
- Modifiers
- Functions

Function declarations should be grouped according to their visibility and ordered:

- constructor
- fallback function (if exists)
- external
- public
- internal
- private

Within a grouping, place the `view` functions last.

## Things to do after creating a project

* Enable CIs, including Travis, Coveralls and BuildKite.
* For BuildKite, set up a command that runs `slither contracts` using the `slither=true` containers.
* Set up CODEOWNERS. The owners should be chosen according to existing project committers / maintainers.
* Set up `master` as a protected branch. Only allow pushing when Travis and Coveralls CI succeed, and require code owners' review, with at least 2 reviews for each PR.
