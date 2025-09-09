Testing
=======

Zstandard CI testing is split up into three sections:
short, medium, and long tests.

Short Tests
-----------
Short tests run on CircleCI for new commits on every branch and pull request.
They consist of the following tests:
- Compilation on all supported targets (x86, x86_64, ARM, AArch64, PowerPC, and PowerPC64)
- Compilation on various versions of gcc, clang, and g++
- `tests/playTests.sh` on x86_64, without the tests on long data (CLI tests)
- Small tests (`tests/legacy.c`, `tests/longmatch.c`) on x64_64

Medium Tests
------------
Medium tests run on every commit and pull request to `dev` branch, on TravisCI.
They consist of the following tests:
- The following tests run with UBsan and Asan on x86_64 and x86, as well as with
  Msan on x86_64
  - `tests/playTests.sh --test-large-data`
  - Fuzzer tests: `tests/fuzzer.c`, `tests/zstreamtest.c`, and `tests/decodecorpus.c`
- `tests/zstreamtest.c` under Tsan (streaming mode, including multithreaded mode)
- Valgrind Test (`make -C tests test-valgrind`) (testing CLI and fuzzer under `valgrind`)
- Fuzzer tests (see above) on ARM, AArch64, PowerPC, and PowerPC64

Long Tests
----------
Long tests run on all commits to `release` branch,
and once a day on the current version of `dev` branch,
on TravisCI.
They consist of the following tests:
- Entire test suite (including fuzzers and some other specialized tests) on:
  - x86_64 and x86 with UBsan and Asan
  - x86_64 with Msan
  - ARM, AArch64, PowerPC, and PowerPC64
- Streaming mode fuzzer with Tsan (for the `zstdmt` testing)
- ZlibWrapper tests, including under valgrind
- Versions test (ensuring `zstd` can decode files from all previous versions)
- `pzstd` with asan and tsan, as well as in 32-bits mode
- Testing `zstd` with legacy mode off
- Entire test suite and make install on macOS
# Commit 7 on Dec 21 - 1767194225
# Commit 10 on Dec 21 - 1767194225
# Commit 12 on Dec 21 - 1767194225
# Commit 11 on Dec 22 - 1767194226
# Commit 14 on Dec 22 - 1767194226
# Commit 17 on Dec 22 - 1767194226
# Commit 5 on Dec 23 - 1767194226
# Commit 6 on Dec 23 - 1767194226
# Commit 8 on Dec 23 - 1767194227
# Commit 9 on Dec 23 - 1767194227
# Commit 11 on Dec 23 - 1767194227
# Commit 23 on Dec 23 - 1767194227
# Commit 11 on Dec 24 - 1767194227
# Commit 14 on Dec 24 - 1767194227
# Commit 5 on Dec 25 - 1767194228
# Commit 17 on Dec 25 - 1767194228
# Commit 8 on Dec 26 - 1767194228
# Commit 12 on Dec 26 - 1767194228
# Commit 15 on Dec 26 - 1767194228
# Commit 5 on Dec 27 - 1767194229
# Commit 9 on Dec 27 - 1767194229
# Commit 11 on Dec 27 - 1767194229
# Commit 4 on Dec 28 - 1767194229
# Commit 6 on Dec 28 - 1767194229
# Commit 12 on Dec 28 - 1767194230
# Commit 30 on Dec 28 - 1767194230
# Commit 9 on Dec 29 - 1767194230
# Commit 10 on Dec 29 - 1767194230
# Commit 19 on Dec 29 - 1767194231
# Commit 20 on Dec 29 - 1767194231
# Commit 23 on Dec 29 - 1767194231
# Commit 12 on Dec 30 - 1767194231
# Commit 1 on Dec 31 - 1767194231
# Commit 24 on Dec 31 - 1767194232
# Commit 32 on Dec 31 - 1767194232
# Commit 33 on Dec 31 - 1767194232
# Commit 4 on Nov 22 - 1767194364
# Commit 12 on Nov 22 - 1767194364
# Commit 19 on Nov 22 - 1767194364
# Commit 4 on Nov 23 - 1767194364
# Commit 7 on Nov 23 - 1767194364
# Commit 3 on Nov 24 - 1767194365
# Commit 7 on Nov 24 - 1767194365
# Commit 20 on Nov 24 - 1767194365
# Commit 11 on Nov 25 - 1767194366
# Commit 15 on Nov 25 - 1767194366
# Commit 22 on Nov 25 - 1767194366
# Commit 2 on Nov 26 - 1767194366
# Commit 13 on Nov 26 - 1767194366
# Commit 20 on Nov 26 - 1767194366
# Commit 7 on Nov 27 - 1767194367
# Commit 8 on Nov 27 - 1767194367
# Commit 14 on Nov 27 - 1767194367
# Commit 8 on Nov 29 - 1767194368
# Commit 11 on Nov 29 - 1767194368
# Commit 15 on Nov 29 - 1767194368
# Commit 27 on Nov 29 - 1767194368
# Commit 4 on Nov 30 - 1767194369
# Commit 7 on Nov 30 - 1767194369
# Commit 16 on Nov 30 - 1767194369
# Commit 25 on Nov 30 - 1767194369
# Commit 2 on Dec 6 - 1767194470
# Commit 3 on Dec 6 - 1767194470
# Commit 7 on Dec 7 - 1767194470
# Commit 9 on Dec 8 - 1767194471
# Commit 5 on Dec 9 - 1767194471
# Commit 4 on Dec 10 - 1767194471
# Commit 2 on Dec 11 - 1767194471
# Commit 5 on Sep 8 - 1767194555
# Commit 9 on Sep 8 - 1767194555
# Commit 11 on Sep 8 - 1767194555
# Commit 15 on Sep 8 - 1767194555
# Commit 17 on Sep 8 - 1767194555
# Commit 13 on Sep 9 - 1767194555
# Commit 16 on Sep 9 - 1767194556
# Commit 17 on Sep 9 - 1767194556
# Commit 21 on Sep 9 - 1767194556
