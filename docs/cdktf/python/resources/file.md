---
page_title: "archive_file Resource - terraform-provider-archive"
subcategory: ""
description: |-
  Generates an archive from content, a file, or directory of files.
---


<!-- Please do not edit this file, it is generated. -->
# archive_file (Resource)

Generates an archive from content, a file, or directory of files.

## Example Usage

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.archive.file import File
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
        File(self, "init",
            output_path="${path.module}/files/init.zip",
            source_file="${path.module}/init.tpl",
            type="zip"
        )
```

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import Token, TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.archive.file import File
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
        File(self, "dotfiles",
            excludes=["${path.module}/unwanted.zip"],
            output_path="${path.module}/files/dotfiles.zip",
            source=[FileSource(
                content=Token.as_string(vimrc.rendered),
                filename=".vimrc"
            ), FileSource(
                content=Token.as_string(ssh_config.rendered),
                filename=".ssh/config"
            )
            ],
            type="zip"
        )
```

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.archive.file import File
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
        File(self, "lambda_my_function",
            output_file_mode="0666",
            output_path="${path.module}/files/lambda-my-function.js.zip",
            source_file="${path.module}/../lambda/my-function/index.js",
            type="zip"
        )
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `output_path` (String) The output of the archive file.
- `type` (String) The type of archive to generate. NOTE: `zip` and `tar.gz` is supported.

### Optional

- `exclude_symlink_directories` (Boolean) Boolean flag indicating whether symbolically linked directories should be excluded during the creation of the archive. Defaults to `false`.
- `excludes` (Set of String) Specify files/directories to ignore when reading the `source_dir`. Supports glob file matching patterns including doublestar/globstar (`**`) patterns.
- `output_file_mode` (String) String that specifies the octal file mode for all archived files. For example: `"0666"`. Setting this will ensure that cross platform usage of this module will not vary the modes of archived files (and ultimately checksums) resulting in more deterministic behavior.
- `source` (Block Set) Specifies attributes of a single source file to include into the archive. One and only one of `source`, `source_content_filename` (with `source_content`), `source_file`, or `source_dir` must be specified. (see [below for nested schema](#nestedblock--source))
- `source_content` (String) Add only this content to the archive with `source_content_filename` as the filename. One and only one of `source`, `source_content_filename` (with `source_content`), `source_file`, or `source_dir` must be specified.
- `source_content_filename` (String) Set this as the filename when using `source_content`. One and only one of `source`, `source_content_filename` (with `source_content`), `source_file`, or `source_dir` must be specified.
- `source_dir` (String) Package entire contents of this directory into the archive. One and only one of `source`, `source_content_filename` (with `source_content`), `source_file`, or `source_dir` must be specified.
- `source_file` (String) Package this file into the archive. One and only one of `source`, `source_content_filename` (with `source_content`), `source_file`, or `source_dir` must be specified.

### Read-Only

- `id` (String) The sha1 checksum hash of the output.
- `output_base64sha256` (String) Base64 Encoded SHA256 checksum of output file
- `output_base64sha512` (String) Base64 Encoded SHA512 checksum of output file
- `output_md5` (String) MD5 of output file
- `output_sha` (String) SHA1 checksum of output file
- `output_sha256` (String) SHA256 checksum of output file
- `output_sha512` (String) SHA512 checksum of output file
- `output_size` (Number) The byte size of the output archive file.

<a id="nestedblock--source"></a>
### Nested Schema for `source`

Required:

- `content` (String) Add this content to the archive with `filename` as the filename.
- `filename` (String) Set this as the filename when declaring a `source`.

<!-- cache-key: cdktf-0.20.8 input-46508f720325fcf13d4a50acef1fde81a72282d7fe681248eae9aa7318fad025 -->