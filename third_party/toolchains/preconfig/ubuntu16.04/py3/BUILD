licenses(["restricted"])

package(default_visibility = ["//visibility:public"])

# To build Python C/C++ extension on Windows, we need to link to python import library pythonXY.lib
# See https://docs.python.org/3/extending/windows.html
cc_import(
    name = "python_lib",
    interface_library = select({
        ":windows": ":python_import_lib",
        # A placeholder for Unix platforms which makes --no_build happy.
        "//conditions:default": "not-existing.lib",
    }),
    system_provided = 1,
)

cc_library(
    name = "python_headers",
    hdrs = [":python_include"],
    includes = ["python_include"],
    deps = select({
        ":windows": [":python_lib"],
        "//conditions:default": [],
    }),
)

cc_library(
    name = "numpy_headers",
    hdrs = [":numpy_include"],
    includes = ["numpy_include"],
)

config_setting(
    name = "windows",
    values = {"cpu": "x64_windows"},
    visibility = ["//visibility:public"],
)

genrule(
    name = "python_include",
    outs = [
        "python_include/Python-ast.h",
        "python_include/Python.h",
        "python_include/abstract.h",
        "python_include/accu.h",
        "python_include/asdl.h",
        "python_include/ast.h",
        "python_include/bitset.h",
        "python_include/bltinmodule.h",
        "python_include/boolobject.h",
        "python_include/bytearrayobject.h",
        "python_include/bytes_methods.h",
        "python_include/bytesobject.h",
        "python_include/cellobject.h",
        "python_include/ceval.h",
        "python_include/classobject.h",
        "python_include/code.h",
        "python_include/codecs.h",
        "python_include/compile.h",
        "python_include/complexobject.h",
        "python_include/datetime.h",
        "python_include/descrobject.h",
        "python_include/dictobject.h",
        "python_include/dtoa.h",
        "python_include/dynamic_annotations.h",
        "python_include/enumobject.h",
        "python_include/errcode.h",
        "python_include/eval.h",
        "python_include/fileobject.h",
        "python_include/fileutils.h",
        "python_include/floatobject.h",
        "python_include/frameobject.h",
        "python_include/funcobject.h",
        "python_include/genobject.h",
        "python_include/graminit.h",
        "python_include/grammar.h",
        "python_include/import.h",
        "python_include/intrcheck.h",
        "python_include/iterobject.h",
        "python_include/listobject.h",
        "python_include/longintrepr.h",
        "python_include/longobject.h",
        "python_include/marshal.h",
        "python_include/memoryobject.h",
        "python_include/metagrammar.h",
        "python_include/methodobject.h",
        "python_include/modsupport.h",
        "python_include/moduleobject.h",
        "python_include/namespaceobject.h",
        "python_include/node.h",
        "python_include/object.h",
        "python_include/objimpl.h",
        "python_include/odictobject.h",
        "python_include/opcode.h",
        "python_include/osdefs.h",
        "python_include/osmodule.h",
        "python_include/parsetok.h",
        "python_include/patchlevel.h",
        "python_include/pgen.h",
        "python_include/pgenheaders.h",
        "python_include/py_curses.h",
        "python_include/pyarena.h",
        "python_include/pyatomic.h",
        "python_include/pycapsule.h",
        "python_include/pyconfig.h",
        "python_include/pyctype.h",
        "python_include/pydebug.h",
        "python_include/pydtrace.h",
        "python_include/pyerrors.h",
        "python_include/pyexpat.h",
        "python_include/pyfpe.h",
        "python_include/pygetopt.h",
        "python_include/pyhash.h",
        "python_include/pylifecycle.h",
        "python_include/pymacconfig.h",
        "python_include/pymacro.h",
        "python_include/pymath.h",
        "python_include/pymem.h",
        "python_include/pyport.h",
        "python_include/pystate.h",
        "python_include/pystrcmp.h",
        "python_include/pystrhex.h",
        "python_include/pystrtod.h",
        "python_include/pythonrun.h",
        "python_include/pythread.h",
        "python_include/pytime.h",
        "python_include/rangeobject.h",
        "python_include/setobject.h",
        "python_include/sliceobject.h",
        "python_include/structmember.h",
        "python_include/structseq.h",
        "python_include/symtable.h",
        "python_include/sysmodule.h",
        "python_include/token.h",
        "python_include/traceback.h",
        "python_include/tupleobject.h",
        "python_include/typeslots.h",
        "python_include/ucnhash.h",
        "python_include/unicodeobject.h",
        "python_include/warnings.h",
        "python_include/weakrefobject.h",
    ],
    cmd = """
    SRCDIR="/usr/include/python3.5m"
    SRCDIR="/opt/python3.6/include/python3.6m"
    for dst in $(OUTS); do
      name="$${dst#*python_include/}"
      src="$${SRCDIR}/$${name}"

      mkdir -p "$${dst%/*}"
      cp -f "$${src}" "$${dst}"
    done
    """,
)

genrule(
    name = "numpy_include",
    outs = [
        "numpy_include/numpy/__multiarray_api.h",
        "numpy_include/numpy/__ufunc_api.h",
        "numpy_include/numpy/_neighborhood_iterator_imp.h",
        "numpy_include/numpy/_numpyconfig.h",
        "numpy_include/numpy/arrayobject.h",
        "numpy_include/numpy/arrayscalars.h",
        "numpy_include/numpy/halffloat.h",
        "numpy_include/numpy/multiarray_api.txt",
        "numpy_include/numpy/ndarrayobject.h",
        "numpy_include/numpy/ndarraytypes.h",
        "numpy_include/numpy/noprefix.h",
        "numpy_include/numpy/npy_1_7_deprecated_api.h",
        "numpy_include/numpy/npy_3kcompat.h",
        "numpy_include/numpy/npy_common.h",
        "numpy_include/numpy/npy_cpu.h",
        "numpy_include/numpy/npy_endian.h",
        "numpy_include/numpy/npy_interrupt.h",
        "numpy_include/numpy/npy_math.h",
        "numpy_include/numpy/npy_no_deprecated_api.h",
        "numpy_include/numpy/npy_os.h",
        "numpy_include/numpy/numpyconfig.h",
        "numpy_include/numpy/old_defines.h",
        "numpy_include/numpy/oldnumeric.h",
        "numpy_include/numpy/ufunc_api.txt",
        "numpy_include/numpy/ufuncobject.h",
        "numpy_include/numpy/utils.h",
    ],
    cmd = """
    SRCDIR="/opt/python3.6/lib/python3.6/site-packages/numpy/core/include"
    for dst in $(OUTS); do
      name="$${dst#*numpy_include/}"
      src="$${SRCDIR}/$${name}"

      mkdir -p "$${dst%/*}"
      cp -f "$${src}" "$${dst}"
    done
    """,
)
