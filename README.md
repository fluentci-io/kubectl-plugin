# Kubectl Plugin

[![fluentci pipeline](https://shield.fluentci.io/x/kubectl)](https://pkg.fluentci.io/kubectl)
[![ci](https://github.com/fluentci-io/kubectl-plugin/actions/workflows/ci.yml/badge.svg)](https://github.com/fluentci-io/kubectl-plugin/actions/workflows/ci.yml)

This plugin sets up your CI/CD pipeline with a specific version of [Kubectl](https://github.com/kubernetes/kubectl).

## 🚀 Usage

Add the following command to your CI configuration file:

```bash
fluentci run --wasm kubectl setup
```

## Functions

| Name     | Description                                        |
| -------- | -------------------------------------------------- |
| setup    | Installs a specific version of kubectl.            |
| apply    | Applies a configuration to the Kubernetes cluster. |

## Code Usage

Add `fluentci-pdk` crate to your `Cargo.toml`:

```toml
[dependencies]
fluentci-pdk = "0.2.1"
```

Use the following code to call the plugin:

```rust
use fluentci_pdk::dag;

// ...

dag().call("https://pkg.fluentci.io/kubectl@v0.1.0?wasm=1", "setup", vec!["latest"])?;
```

## 📚 Examples

Github Actions:

```yaml
- name: Setup Fluent CI CLI
  uses: fluentci-io/setup-fluentci@v5
  with:
    wasm: true
    plugin: kubectl
    args: |
      setup
- name: Show kubectl version
  run: |
    type kubectl
    kubectl version --client=true
```
