# Install brew command

> Run terminal and then first, issue an update command-



```
sudo apt update
```
```
sudo apt-get install build-essential
```

> Run Homebrew installation script

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> To run the brew command after installation, we need to add it to our system path…

```
(echo; echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"') >> /home/user/.bashrc
```
```
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```
> To ensure everything is working correctly to use brew, we can run its command-

```
brew doctor
```
# Installation of AIac by Firefly

```
brew install gofireflyio/aiac/aiac
```
# EXPORT API key


```
export OPENAI_API_KEY=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
```
---

## Use Cases and Example Prompts

### Generate IaC

- `aiac get terraform for a highly available eks`
- `aiac get pulumi golang for an s3 with sns notification`
- `aiac get cloudformation for a neptundb`

### Generate Configuration Files

- `aiac get dockerfile for a secured nginx`
- `aiac get k8s manifest for a mongodb deployment`

### Generate CI/CD Pipelines

- `aiac get jenkins pipeline for building nodejs`
- `aiac get github action that plans and applies terraform and sends a slack notification`

### Generate Policy as Code

- `aiac get opa policy that enforces readiness probe at k8s deployments`

### Generate Utilities

- `aiac get python code that scans all open ports in my network`
- `aiac get bash script that kills all active terminal sessions`

### Command Line Builder

- `aiac get kubectl that gets ExternalIPs of all nodes`
- `aiac get awscli that lists instances with public IP address and Name`

### Query Builder

- `aiac get mongo query that aggregates all documents by created date`
- `aiac get elastic query that applies a condition on a value greater than some value in aggregation`
- `aiac get sql query that counts the appearances of each row in one table in another table based on an id column`

---

### Usage

1. Create your OpenAI API key [here](https://platform.openai.com/account/api-keys).
2. Click “Create new secret key” and copy it.
3. Provide the API key via the `OPENAI_API_KEY` environment variable or via the `--api-key` command line flag.

#### Command Line

By default, aiac prints the extracted code to standard output and opens an
interactive shell that allows retrying requests, enabling chat mode (for chat
models), saving output to files, copying code to clipboard, and more:

    aiac get terraform for AWS EC2

You can ask it to also store the code to a specific file with a flag:

    aiac get terraform for eks --output-file=eks.tf

You can use a flag to save the full Markdown output as well:

    aiac get terraform for eks --output-file=eks.tf --readme-file=eks.md

If you prefer aiac to print the full Markdown output to standard output rather
than the extracted code, use the `-f` or `--full` flag:

    aiac get terraform for eks -f

You can use aiac in non-interactive mode, simply printing the generated code
to standard output, and optionally saving it to files with the above flags,
by providing the `-q` or `--quiet` flag:

    aiac get terraform for eks -q

By default, aiac uses the gpt-3.5-turbo chat model, but other models are
supported, including gpt-4. You can list all supported models:

    aiac list-models

To generate code with a different model, provide the `--model` flag:

    aiac get terraform for eks --model="text-davinci-003"

#### Via Docker

All the same instructions apply, except you execute a `docker` image:

    docker run \
        -it \
        -e OPENAI_API_KEY=[PUT YOUR KEY HERE] \
        ghcr.io/gofireflyio/aiac get terraform for ec2

#### As a Library

You can use aiac as a library:

```go
package main

import (
    "context"
    "os"

    "github.com/gofireflyio/aiac/v3/libaiac"
)

func main() {
    client := libaiac.NewClient(os.Getenv("OPENAI_API_KEY"))
    ctx    := context.TODO()

    // use the model-agnostic wrapper
    res, err := client.GenerateCode(
        ctx,
        libaiac.ModelTextDaVinci3,
        "generate terraform for ec2",
    )
    if err != nil {
        fmt.Fprintf(os.Stderr, "Failed generating code: %s\n", err)
        os.Exit(1)
    }

    fmt.Fprintln(os.Stdout, res.Code)

    // use the completion API (for completion-only models)
    res, err = client.Complete(
        ctx,
        libaiac.ModelTextDaVinci3,
        "generate terraform for ec2",
    )

    // converse via a chat model
    chat := client.Chat(libaiac.ModelGPT35Turbo)
    res, err = chat.Send(ctx, "generate terraform for eks")
    res, err = chat.Send(ctx, "region must be eu-central-1")
}
```
