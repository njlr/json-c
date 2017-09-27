# Rather than call autotools, we create a dummy config.h
# and then pass in the appropriate flags deterministically.
# https://buckaroo.pm

genrule(
  name = 'config',
  out = 'config.h',
  cmd = 'touch $OUT',
  visibility = [
    '//...',
  ],
)

macos_preprocessor_flags = [
  '-DHAVE_ATOMIC_BUILTINS=1',
  '-DHAVE_DECL_INFINITY=1',
  '-DHAVE_DECL_ISINF=1',
  '-DHAVE_DECL_ISNAN=1',
  '-DHAVE_DECL_NAN=1',
  '-DHAVE_DECL__FINITE=0',
  '-DHAVE_DECL__ISNAN=0',
  '-DHAVE_DLFCN_H=1',
  '-DHAVE_FCNTL_H=1',
  '-DHAVE_INTTYPES_H=1',
  '-DHAVE_LIMITS_H=1',
  '-DHAVE_LOCALE_H=1',
  '-DHAVE_MEMORY_H=1',
  '-DHAVE_OPEN=1',
  '-DHAVE_REALLOC=1',
  '-DHAVE_SETLOCALE=1',
  '-DHAVE_SNPRINTF=1',
  '-DHAVE_STDARG_H=1',
  '-DHAVE_STDINT_H=1',
  '-DHAVE_STDLIB_H=1',
  '-DHAVE_STRCASECMP=1',
  '-DHAVE_STRDUP=1',
  '-DHAVE_STRERROR=1',
  '-DHAVE_STRINGS_H=1',
  '-DHAVE_STRING_H=1',
  '-DHAVE_STRNCASECMP=1',
  '-DHAVE_SYSLOG_H=1',
  '-DHAVE_SYS_CDEFS_H=1',
  '-DHAVE_SYS_PARAM_H=1',
  '-DHAVE_SYS_STAT_H=1',
  '-DHAVE_SYS_TYPES_H=1',
  # ...
  '-DHAVE_VASPRINTF=1',
  # ...
  '-DHAVE_XLOCALE_H=1',
  # ...
  '-DSIZEOF_INT=4',
  '-DSIZEOF_INT64_T=8',
  '-DSIZEOF_LONG=8',
  '-DSIZEOF_LONG_LONG=8',
  '-DSIZEOF_SIZE_T=8',
  # ...
  '-DPACKAGE_VERSION="0.12.99"',
  '-DVERSION="0.12.99"',
]

cxx_library(
  name = 'json-c',
  header_namespace = '',
  exported_headers = subdir_glob([
    ('', '*.h'),
  ]),
  headers = {
    'config.h': ':config',
  },
  srcs = glob([
    '*.c',
  ]),
  platform_preprocessor_flags = [
    ('default', macos_preprocessor_flags),
    ('^macos.*', macos_preprocessor_flags),
  ],
  visibility = [
    'PUBLIC',
  ],
)
