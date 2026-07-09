# Tau SDK for Workshop

This SDK provides the [Tau](https://github.com/huggingface/tau) AI coding agent
for use within a workshop. Session history, provider credentials, and user
configuration stored under `~/.tau` are persisted on the host across workshop
updates.

---

## Reference workshop

A minimal workshop:

```yaml
# workshop.yaml
name: my-project
base: ubuntu@24.04
sdks:
  - name: tau
    channel: latest/stable
```

This gives you the `tau` CLI on PATH inside the workshop. Run `tau` from your
project directory to start an interactive coding session.

---

## Using the SDK

### Prerequisites, project layout

1. No prerequisite SDKs are required.
2. No specific project layout is needed — run `tau` from any directory.
3. On first launch, the SDK creates a Python virtual environment under
   `~/.tau/venv` and installs `tau-ai`. Subsequent launches skip the install
   if the version is already present. Provider credentials set via `/login`
   inside Tau are stored in `~/.tau` and survive workshop updates.

### Start a coding session

```bash
workshop shell
cd /project
tau
```

Connect a model provider on first use:

```text
/login
/model
```

### One-shot print mode

```bash
workshop shell
tau -p "summarize the architecture"
```

### Verify from the command line

```bash
workshop shell
tau --version
```

---

## Plugs (resources this SDK consumes)

### `tau-data`

- Interface: `mount`
- Workshop target: `/home/workshop/.tau`
- Purpose: Persists session history (JSONL), provider credentials, and user
  configuration across workshop updates. Also holds the Python virtual
  environment used to run Tau.

---

## Slots (resources this SDK provides)

This SDK doesn't define any slots.

---

## Documentation and guidance

- [Tau documentation](https://twotimespi.dev/)
- [Tau quickstart](https://twotimespi.dev/quickstart/)
- [Providers and models guide](https://twotimespi.dev/guides/providers-and-models/)

---

## Community and support

- Tau issues and discussions:
  [github.com/huggingface/tau/issues](https://github.com/huggingface/tau/issues)

---

## Contributions

All contributions, including code, documentation updates, and issue reports,
are welcome!

- Open issues or pull requests on the
  [tau-workshop-sdk repository](https://github.com/canonical/tau-workshop-sdk).

---

## License and copyright

The SDK scripts in this repository are copyright their respective contributors.

Tau (`tau-ai`) is released under the
[MIT License](https://github.com/huggingface/tau/blob/main/LICENSE).
