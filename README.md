# metronome-audio-to-midi
JUCE plugin (vst3 or standalone) that converts the inputted metronome audio stream and converts it to a midi clock output.

currently displays current system time in milliseconds & current hardware time from boot in milliseconds.

todo:
- generate simple clock output as midi and audio
- sync to input clock audio or midi
- sync beat to current system time
- implement "Simple Network Time Protocol" (SNTPv4) as described in https://tools.ietf.org/html/rfc4330 particularly page 13:

   When the server reply is received, the client determines a
   Destination Timestamp variable as the time of arrival according to
   its clock in NTP timestamp format.  The following table summarizes
   the four timestamps.

      Timestamp Name          ID   When Generated
      ------------------------------------------------------------
      Originate Timestamp     T1   time request sent by client
      Receive Timestamp       T2   time request received by server
      Transmit Timestamp      T3   time reply sent by server
      Destination Timestamp   T4   time reply received by client

   The roundtrip delay d and system clock offset t are defined as:

      d = (T4 - T1) - (T3 - T2)     t = ((T2 - T1) + (T3 - T4)) / 2.
