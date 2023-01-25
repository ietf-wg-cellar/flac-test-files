This README is for the 'faulty' files of the FLAC decoder
testbench. Please read the README in the top level directory
first.

- File 01 has a streaminfo metadata block that lists the wrong
  maximum blocksize for the file. The file has a fixed
  blocksize of 16384 samples, but the streaminfo metadata block
  says the maximum blocksize is 4096. When a decoder
  initializes buffers for a blocksize of 4096 and tries to
  decode a block with 16384 samples, it might overrun a buffer

- File 02 has a streaminfo metadata block that lists the wrong
  maximum framesize for the file. The file has an actual
  maximum framesize of 8846 byte, but the streaminfo metadata
  block says the maximum framesize is 654 byte. When a decoder
  initializes buffers for a frames of at most 654 byte and
  tries to read a frame of 8846 byte, it might overrun a buffer

- File 03 has a streaminfo metadata block that lists the wrong
  bit depth for the file. It says the bit depth is 24, but the
  actual bit depth of all frames is 16.

- File 04 has a streaminfo metadata block that lists the wrong
  number of channels for the file. It says the number of
  channels is 5, but the actual number of channels is 1.

- File 05 has a streaminfo metadata block that lists the wrong
  total number of samples. It says the number of samples is
  39842, while the actual total number of samples is 109487

- File 06 doesn't have a streaminfo metadata block, despite
  having other metadata blocks, unlike the files 10 and 11 in
  the 'uncommon' set of files, which start directly at a frame
  header. It does have two other metadata blocks, a vorbis
  comment block and a padding block

- File 07 has a streaminfo metadata block that is not the first
  metadata block of the file. It is being preceded by two other
  metadata blocks, a vorbis comment block and a padding block

- File 08 has a blocksize of 65536, which is representable by
  the frame header but not by the streaminfo metadata block,
  and is thus invalid

- File 09 has a blocksize of 1, which is not allowed for all
  but the last frame of a file

- File 10 has a vorbis comment metadata block with invalid
  contents. The block has a correct overall length and has a
  single tag, but it states there are 10 tags, which means a
  parser could overread the block if it does not check for
  validity.

- File 11 has an incorrect metadata block length, which leads
  to the parser searching for the next metadata block reading
  garbage.
