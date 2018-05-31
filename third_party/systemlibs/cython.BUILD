licenses(["notice"])  # Apache-2.0

# find cython.py in python site-packages. $PYTHON_LIB_PATH is not defined here.
genrule(
    name = "cpcython",
    outs = ["cython.py"],
    cmd = """
    for i in /usr/lib*/python*/site-packages/cython.py; do
      if [[ -f $$i ]]; then
        cp $$i $@
        break
      fi
    done""",
)

sh_binary(
    name = "cython_binary",
    srcs = ["cython.py"],
    visibility = ["//visibility:public"],
)
