# FormulaTransformEngine

**Deterministic formula transformations for mathematical expressions and functional analysis.**

`FormulaTransformEngine` is a core symbolic engine originally developed as part of the Math Copilot project and now maintained as an independent Wolfram Language Paclet. It provides a robust, strongly-typed Intermediate Representation (IR) for executing deterministic mathematical transformations on expressions, integral estimates, and functional analysis topologies.

## Key Features

* **Typeclass-like Properties**: Inspired by formal theorem provers (like Lean 4 and Coq), algebraic operators are decoupled from measure-theoretic properties. Generic operators (e.g., `Integral`) are combined with formal properties (e.g., `FunctionSpace`, `Measurable`) rather than relying on brittle hardcoded syntax.
* **Functional Analysis Primitives**: Built-in native understanding of abstract spaces and norms, such as Lebesgue spaces ($L^p$) and Sobolev spaces ($W^{k,p}$).
* **Inactive Computation**: Intelligently skirts Wolfram Language's aggressive auto-evaluation engine using `Inactive` forms and bespoke capitalized primitives to prevent formulas from collapsing before they are formally matched.
* **Target-Guided Planners & Heuristics**: Supports one-shot transform planning and structurally-aware previews without mutating the underlying JSON rule registries.
* **Formal System Export Compatibility**: Strict adherence to the Copilot IR allows seamless exportation of these transformation rules into systems like Lean 4 (e.g. mapping `Integral` to `measure_theory.integral`).

## Installation

As a standard Wolfram Language Paclet, you can install the engine directly from this repository.

1. Clone the repository:
   ```bash
   git clone https://github.com/Lightmarey/FormulaTransformEngine.git
   ```
2. In Mathematica or Wolfram Language, install the paclet directory:
   ```mathematica
   PacletInstall["/path/to/FormulaTransformEngine"]
   ```
3. Load the package:
   ```mathematica
   Needs["FormulaTransformEngine`"]
   ```

*(Note: If published to the Wolfram Paclet Repository in the future, it will be available directly via `PacletInstall["MathCopilot/FormulaTransformEngine"]`)*

## Usage

Rules and heuristics are loaded securely from the encapsulated `Registry` asset.

```mathematica
(* Inspect the loaded transform rules and heuristics *)
InspectFormulaTransformRegistry[]

(* Apply a specific rule to an inactive integral expression *)
state = ApplyFormulaTransform["IntegrationByParts", <||>][expr];
```

For more details on the internal syntax and allowed primitives, please see [`PRIMITIVES_AND_SYNTAX.md`](PRIMITIVES_AND_SYNTAX.md). Documentation for individual symbols can be accessed via the Wolfram Documentation Center once the paclet is loaded.

## License

This project is licensed under the **Business Source License 1.1 (BSL-1.1)**.
You may use the software for non-production purposes, testing, and development. Please refer to the [`LICENSE`](LICENSE) file for exact terms, the Additional Use Grant, and the Change Date details.
