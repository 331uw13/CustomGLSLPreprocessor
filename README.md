# CustomGLSLPreprocessor
## "#include" preprocessor for GLSL.

* Usage:
```c
#include <stdio.h>
#include <stdlib.h>

#include "glsl_preproc.h"

int main() {
    struct file_t fragment_file;
    if(!read_file(&fragment_file, "test.fs")) {
        return 1;
    }

    size_t sizeout = 0;
    char* glsl = preproc_glsl(&fragment_file, &sizeout);
    printf("-----\n\033[90m%s\n\033[0m-----\n", glsl);
    printf("\033[32m'preproc_glsl' returned: %p, %li\033[0m\n", glsl, sizeout);

    // -> Here you could compile and link the shader programs
    // ...

    if(glsl) {
        free(glsl);
    }
    close_file(&fragment_file);
    return 0;
}
```
