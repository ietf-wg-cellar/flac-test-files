This readme belongs to a collection of FLAC files that can be
used to test various FLAC decoder abilities.

For all files in this testbench:

---------------------------------------------------------------
FLAC decoder testbench by Martijn van Beurden

To the extent possible under law, the person who associated CC0
with FLAC decoder testbench has waived all copyright and
related or neighboring rights to FLAC decoder testbench.

You should have received a copy of the CC0 legalcode along with
this collection as a file called LICENSE.txt. If not, see
<http://creativecommons.org/publicdomain/zero/1.0/>
---------------------------------------------------------------

The files in this testbench are split up in groups. Each group
is placed in its own directory and has its own README
explaining what each file is supposed to test. This README
will explain on a higher level what the purpose is of testing
with the files of that group

---------------------------------------------------------------
                         Group subset
           Files that any user might try to playback
---------------------------------------------------------------

The FLAC format specifies a subset of itself to ensure
streamability and limits the decoding requirements for hardware
implementations. The reference FLAC encoder will enforce this
subset unless specifically disabled.

The files in this group are considered a baseline for general
decoders: these files should be properly decoded or properly
rejected before playback is attempted by any decoder. A
decoder can choose to reject certain files, for example
multichannel files, files with high or unusual samplerates,
files with a high bit depth. Crashing or mangled playback of
these files is probably going to be noticed by unsuspecting
users of a decoder. Read the README.txt in the directory
subset for details on each file.

On Hydrogenaud.io there is a wikipage and a forum discussion
devoted to this testbench group. The wikipage might be useful
for comparison to other decoders, and the forum is a good place
to ask questions. See:
https://wiki.hydrogenaud.io/index.php?title=FLAC_decoder_testbench
and https://hydrogenaud.io/index.php?topic=121478.0

---------------------------------------------------------------
                         Group uncommon
   Files with uncommon or exotic features of the FLAC format
---------------------------------------------------------------

Certain features of the FLAC format are non-subset or otherwise
uncommonly used. Decoders might not be able to playback these
files, but they should detect this inability and preferably
notify the user rather than crash of freeze.
