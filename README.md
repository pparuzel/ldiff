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

### File-to-file comparison
```bash
$ ldiff file1 file2
Levenshtein comparison of file1 (S=5345)
file2: 100.00% similar. D=0, S=5345
```

### File-to-directory comparison
```bash
$ ldiff vars/Pipeline.groovy .
Levenshtein comparison of vars/Pipeline.groovy (S=12104)
vars is a directory, skipping...
./Jenkinsfile.sanitizer: 54.35% similar. D=5525, S=10352
./Jenkinsfile.master: 42.09% similar. D=8171, S=14110
./Jenkinsfile.dev: 0.62% similar. D=12029, S=76
```

### File-to-subdirectories comparison (recursive)
```bash
$ ldiff -r vars/Pipeline.groovy .
Levenshtein comparison of vars/Pipeline.groovy (S=12104)
./vars/Pipeline.groovy: 100.00% similar. D=0, S=12104
./Jenkinsfile.sanitizer: 54.35% similar. D=5525, S=10352
./Jenkinsfile.master: 42.09% similar. D=8171, S=14110
./Jenkinsfile.dev: 0.62% similar. D=12029, S=76
```

### Only displaying results equal to or above a certain threshold
```bash
$ ldiff -r vars/Pipeline.groovy . -t 40
Levenshtein comparison of vars/Pipeline.groovy (S=12104)
./vars/Pipeline.groovy: 100.00% similar. D=0, S=12104
./Jenkinsfile.sanitizer: 54.35% similar. D=5525, S=10352
./Jenkinsfile.master: 42.09% similar. D=8171, S=14110
```

### Difference (dissimilarity) results
```bash
$ ldiff -r vars/Pipeline.groovy . -d
Levenshtein comparison of vars/Pipeline.groovy (S=12104)
./vars/Pipeline.groovy: 0.00% different. D=0, S=12104
./Jenkinsfile.sanitizer: 45.65% different. D=5525, S=10352
./Jenkinsfile.master: 57.91% different. D=8171, S=14110
./Jenkinsfile.dev: 99.38% different. D=12029, S=76
```
