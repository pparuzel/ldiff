# ldiff
📊 File similarity measuring utility based on Levenshtein distance

# Usage

```bash
$ ldiff --help
usage: ldiff [-h] [-r] [-d] [-t P] file comparisons [comparisons ...]

positional arguments:
  file                 File to compare with
  comparisons          Files or directories to compare

options:
  -h, --help           show this help message and exit
  -r, --recursive      Recursively compare files of unspecified subdirectories
  -d, --different      Show percentage of difference rather than similarity
  -t P, --threshold P  Filter results of equal or higher percentage threshold
```

## Example

```bash
$ ldiff -r vars/Pipeline.groovy .
Levenshtein comparison of vars/Pipeline.groovy (S=12104)
./vars/Pipeline.groovy: 100.00% similar. D=0, S=12104
./Jenkinsfile.sanitizer: 54.35% similar. D=5525, S=10352
./Jenkinsfile.master: 42.09% similar. D=8171, S=14110
./Jenkinsfile.dev: 0.62% similar. D=12029, S=76

$ ldiff -r vars/Pipeline.groovy . -t 40
Levenshtein comparison of vars/Pipeline.groovy (S=12104)
./vars/Pipeline.groovy: 100.00% similar. D=0, S=12104
./Jenkinsfile.sanitizer: 54.35% similar. D=5525, S=10352
./Jenkinsfile.master: 42.09% similar. D=8171, S=14110
```
