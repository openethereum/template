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

## Things to do after creating a project

* Enable CIs, including Travis, Coveralls and BuildKite.
* For BuildKite, set up a command that runs `slither contracts` using the `slither=true` containers.
* Set up CODEOWNERS. The owners should be chosen according to existing project committers / maintainers.
* Set up `master` as a protected branch. Only allow pushing when Travis and Coveralls CI succeed, and require code owners' review, with at least 2 reviews for each PR.
