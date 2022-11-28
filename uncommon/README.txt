This README is for the 'uncommon' files of the FLAC decoder
testbench. Please read the README in the top level directory
first.

- File 01 has a sample rate that changes mid-stream. The file
  starts with a sample rate of 32kHz and switches to 24kHz,
  16kHz and finally 48kHz.

- File 02 has a number of channels that increases mid-stream.
  The file starts with 1 channel, changes to stereo and ends
  with 6 channels.

- File 03 has a number of channels decreases mid-stream. It
  starts with 4 channels, changes to stereo and ends with
  1 channel.

- File 04 has a bit depth that changes mid-stream. It starts
  with a bit depth of 16, changes to 8 and ends with 24.

- File 05 has a bit depth of 32 bit per sample.

- File 06 has a sample rate of 768kHz. Because this sample
  rate cannot be described in the FLAC frame header, files
  with this sample rate are not streamable and not subset.

- File 07 has a bit depth of 15 bit per sample. Because this
  bit depth cannot be described in the FLAC frame header,
  files with this bit depth are not streamable and not subset.

- File 08 has a block size of 65535 samples, which is the
  largest possible block size in FLAC. File using such large
  blocks are not subset.

- File 09 has one subframe with a rice partition order of 15,
  which is the highest possible partition order. In effect
  it means each partition in that subframe contains only a
  single sample. Such an extreme might trigger peculiar
  behaviour in a decoder.

- File 10 is a FLAC file that starts directly at a frame
  header, which means the fLaC marker is absent and no
  metadata is present either. While this is not a recommended
  format to store audio data in, it simulates the way a FLAC
  stream is received when multicast. Additionally, the frame
  numbers of the frames in the stream are rather high which
  can happen when streaming uninterrupted for a long time.

- File 11 is similar in purpose to file 10, but this file has
  unparsable data preceding the first FLAC frame header. This
  better simulates receiving a multicast FLAC stream, because
  the first received packet of a multicast stream might not
  align with a frame boundary, as a frame might be split over
  several packets.
