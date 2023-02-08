This README is for the subset files of the FLAC decoder
testbench. Please read the README in the top level directory
first.

On Hydrogenaud.io there is a wikipage and a forum discussion
devoted to these files. The wikipage might be useful for
comparison to other decoders, and the forum is a good place to
ask questions. See:
https://wiki.hydrogenaud.io/index.php?title=FLAC_decoder_testbench
https://hydrogenaud.io/index.php?topic=121478.0

---------------------------------------------------------------
                       Files # 1 - # 27
      Stereo audio with samplerates no larger than 44.1kHz
             and bit-depths no larger than 16-bit
                  All features within subset
---------------------------------------------------------------

The first 10 files tests 44.1kHz, 16-bit audio with various
blocksizes that are within subset.

Files 11 through 23 tests the ability to decode FLAC files
with various features that are within subset but aren't used
often.

- File 11 uses the maximal allowed rice partition order (8)
- File 12 uses the maximal allowed qlp precision (15)
- File 13 uses the smallest sane qlp precision (2)
- File 14 uses wasted bits
- File 15 uses only 'verbatim' frames
- File 16 uses rice escape codes and partition order 8
- File 17 uses all possible fixed orders (especially order 0
      which isn't used often)
- File 18 is encoded with precision search, using qlp
      precisions between 3 and 15
- File 19 uses a samplerate of 35467Hz
- File 20 uses a samplerate of 39kHz
- File 21 uses a samplerate of 22050Hz
- File 22 has 12 bits per sample
- File 23 has 8 bits per sample

Files 24 through 27 test the ability to decode a FLAC file with
a variable blocksize. This is a subset feature which is
currently (August 2021) only implemented in the Flake decoder
and its forks/decendants and is not enabled by default.

With the release of FLAC 1.2.0 in July 2007, the FLAC
specification was augmented to more clearly signal variable
blocksize streams by the use of a special bit in the header.
File 24, 25 and 26 use this format. File 27 follows the old
specification, which is much harder to detect

- File 24 uses the current format and is created by flake r264
- File 25 uses the current format and is created by a modified
      flake r264 creating smaller blocks
- File 26 uses the current format and is created by
      CUETools.Flake 2.1.6
- File 27 uses the old format and is created by flake 0.11

---------------------------------------------------------------
                       Files # 28 - # 37
      'High-resolution' audio, all features within subset
---------------------------------------------------------------

Files 28 through 37 test the ability to decode various
high-resolution FLAC file (96kHz, 24-bit)

- File 28 uses default settings
- File 29 uses the largest allowed blocksize (16384)
- File 30 uses non-standard blocksize 13456
- File 31 uses only 32th order predictors
- File 32 uses escape codes and partition order 8
- File 33 is upsampled to 192kHz
- File 34 is upsampled to 192kHz, uses blocksize 16384, 32th
    order predictors only, maximum LPC precision and maximum
    partition order
- File 35 uses non-standard samplerate 134560Hz
- File 36 is upsampled to 384kHz
- File 37 has 20 bits per sample

---------------------------------------------------------------
                       Files # 38 - # 44
           Surround sound, all features within subset
---------------------------------------------------------------

Files 38 through 43 test the ability to decode various
multichannel FLAC files. Each file contains a voice description
of the channels present, so as to see whether the channels are
decoded in the correct lay-out.

- File 38 is 3.0-channel (left, right, center)
- File 39 is 4.0-channel or quadraphonic
- File 40 is 5.0-channel
- File 41 is 5.1-channel
- File 42 is 6.1-channel
- File 43 is 7.1-channel

File 44 tests the ability to decode a file with the highest
possible data input per second, staying within subset and using
a standard samplerate. It also only uses 32th order predictors
at the highest possible predictor precision and the largest
blocksize allowed within the FLAC subset making it especially
challenging to decode.

---------------------------------------------------------------
                       Files # 45 - # 59
                       Metadata extremes
---------------------------------------------------------------

Files 45 through 59 test the ability to handle various streams
with valid but rather unusual or extreme metadata.

- File 45 has 'unknown number of samples' in STREAMINFO
- File 46 has maximum and minimum framesize set to 'unknown'
- File 47 has only a STREAMINFO block
- File 48 has an extremely large SEEKTABLE
- File 49 has an extremely large PADDING block
- File 50 has an extremely large PICTURE block (JPG of 15.8MB)
- File 51 has an extremely large VORBISCOMMENT block
- File 52 has an extremely large APPLICATION block
- File 53 has a CUESHEET block with absurdly many indexes
- File 54 with the same 20 VORBISCOMMENTs repeated 1000 times
- File 55 has the metadata of track 47-52 combined
- File 56 has a PICTURE with mimetype image/jpeg
- File 57 has a PICTURE with mimetype image/png
- File 58 has a PICTURE with mimetype image/gif
- File 59 has a PICTURE with mimetype image/avif

---------------------------------------------------------------
                       Files # 60 - # 64
                Miscellaneous, later additions
---------------------------------------------------------------
- File 60 is mono audio
- File 61, 62 and 63 are signals with rather extreme
    characteristics that might trigger overflow if a decoder
    uses 32-bit integers to calculate the predictor where 64-bit
    integers are appropriate
- File 64 contains rice codes with escape code zero
