
                               NMEA to KMZ Utility

                              NMEA2KMZ.exe Ver2.20

                               Jul. 2011 (C)4river
                         http://homepage2.nifty.com/k8/gps/

Summary.
  Convert an NMEA log file of a GPS receiver into KML(Keyhole Markup Language)
  or KMZ file which compressed KML in a ZIP form for Google Earth.
  Moreover, the output by CSV, GPX and NMEA format is also possible.

  The following GPS log file can be converted.
    Wintec: WBT-200, WBT-201, WBT-202, WSG-1000
    RoyalTek: RBT-3000
    Transystem: i-Blue series
    Qstarz: BT-Q1000, BT-Q100X
    HOLUX: M-241
    Columbus: V-900
    VISIONTAC: VGPS-900
    Hanwha: Pocket GPS S1 (PG-S1)


  Operating condition.
    Operational OS:  Windows 7, Window Vista, Windows XP.


Feature.

  1)Can choose the output of four format of KMZ, KML, GPX, NMEA and CSV.
  2)Track point can output information (KMZ, KML).
    At data number, date, time, latitude, longitude, speed, altitude by the choice output.
    Can change a unit of speed in Km/h, mph and kt.
    Convert the time into local time and can output it.
  3)Can choose an icon of a Track point (Four kinds in correspondence with Speed) (KMZ, KML).
    The external icon file can be used.
  4)Can select a Line color, opacity and Line width of a Track (KMZ, KML).
  5)Select the multiple files and batch conversion is possible.
  6)Command-Line option and Drag & Drop are supported.
    The plural beforehand configuration file is prepared, and both data files are good at
    drag & drop.
    Two or more short cuts are prepared, and the configuration file of a different condition
    can be specified for the command line option.
  7)Output by a 3D mode is possible and detailed output condition can be set (KMZ, KML).
    It is possible to display it by replacing the speed with altitude.
  8)The range of the output is definable at time.
  9)On/Off can output Track and Placemark (KMZ, KML).
 10)The icon that the user made for the Placemark icon can be used.
 11)The logo image that the user made for the title can be displayed.
 12)The user can add the judgment condition and the function of GPS.
 13)The geoid value can be correct by using the geoid grid data according to the latitude longitude.
 14)Because the installation is unnecessary, it is possible to execute it on USB memory.


Install.
  In installation just copies executable file NME2KMZ.exe in the suitable folder.
  Because registry is not used, it can Un-install with only the deletion of NME2KMZ.exe
  and NME2KMZ.ini.
  To correct the geoid, it is necessary to acquire the geoid grid data separately and to copy
  it onto the same folder as NME2KMZ.exe (Another folder can be specified with "GeoidPath" of the
  [Geoid] section of the configuration file).
  It is possible to use it by doing a necessary area from EGM2008 in the clip by using the "CustomGeoid"
  utility

  The acquisition of geoid grid data.
    EGM2008 2.5'x2.5': 
      National Geospatial-Intelligence Agency (NGA)
      NGA: EGM2008 - WGS 84 Version
      http://earth-info.nga.mil/GandG/wgs84/gravitymod/egm2008/egm08_wgs84.html
      2.5 x 2.5-Minute Geoid Undulation Grid in WGS 84 - SMALL ENDIAN
      "Und_min2.5x2.5_egm2008_isw=82_WGS84_TideFree_SE.gz" is decompression and
      "Und_min2.5x2.5_egm2008_isw=82_WGS84_TideFree_SE" (149,368,328byte) is obtained.
    EGM2008 1'x1':
      National Geospatial-Intelligence Agency (NGA)
      NGA: EGM2008 - WGS 84 Version
      http://earth-info.nga.mil/GandG/wgs84/gravitymod/egm2008/egm08_wgs84.html
      1 x 1-Minute Geoid Undulation Grid in WGS 84 - SMALL ENDIAN
      "Und_min1x1_egm2008_isw=82_WGS84_TideFree_SE.gz" is decompression and
      "Und_min1x1_egm2008_isw=82_WGS84_TideFree_SE" (933,292,808) is obtained.
         Note)Because the difference with EGM2008 2.5'x2.5' is about less than 3.5mm,
              2.5'x2.5' is usually enough.
    GSIGEO 2000:
      CD-ROM of Geographical Survey Institute is obtained or it downloads it from the Web site.
      Geographical Survey Institute "Geoid 2000 in Japan" geoid model data
      http://vldb.gsi.go.jp/sokuchi/geoid/download/down.html
      http://vldb.gsi.go.jp/sokuchi/geoid/download/agreement.html
      "gsigeoid_ver5_asc.zip" is unzipping and "gsigeome_ver5.asc"(19,670,776byte) under
      the "program" folder is used.


Usage.

1.Specification of an input file name.
  Input a file name of an source file into a part of "File name" of "Input file".
  When two or more files are specified, it delimits by semicolon ";" and it inputs.

  Open dialog opens when click a button of the right-side end.
  Batch conversion can be done by selecting two or more files.
  Can choose a kind of a file in a Pull-down list of "File of type:".

2.Execution of conversion.
  Start conversion when click "Convert" button.
  It is success if displayed with "*** Completed: filename xxx records ***  xx files" by
  a status bar of the screen lower part.
  Display a detailed report when clicked "Report" of the screen lower.
  Execution is aborted by "Esc" key.

  An output file is made in a folder same as an input file.
  A file name adds extension name .kml .kmz .gpx or .nmea at the data time and makes it.
    Note) When there is a file of a file name same as an output file, it is overwritten.

  When the log file of "Hanwha Pocket GPS S1 (PG-S1)" is input, the latitude longitude and
  the reference height when the log begins are displayed, and the input of an actual altitude
  and the temperature of this point is requested.
  In this case, the corrected altitude and barometric pressure can be output in data.
    Note 1) There is a possibility for it to become impossible to use by the firmware update
            (confirmed by 10.04.23).
    Note 2) The error margin increases in the log of a long time
            because the barometric pressure and the temperature may changes at time.
    Note 3) This function can be stopped by changing "UseBarometer=1" of the [PG-S1] section
            of the configuration file to "UseBarometer=0".
    Note 4) The offset value for the barometric pressure correction can be set to
            "BarometerOffset" of the [PG-S1] section of the configuration file.
    Note 5) The temperature compensating is simply corrected with the temperature profile
            6.5 degrees C/Km (Base value: 1013.25hPa=0m at 15degrees C).

3.Option setting.

  1)Use Fix only.
    Only the data that GPS valid is converted (NMEA, i-Blue series, Qstarz BT-Q1000).

  2)Use Estim.
    Output the data of the Estimated (dead reckoning).

  3)Split Time.
    Appoint omission time for input data to divide an output file into a case except
    WBT-100, 200, 201, 202, WSG-1000.
    Setting is not possibility less than for 0.25minute(15 seconds).

  4)Mask.
    When checking it, Data is output only when HDOP is below a specified value and 
    the number of use satellites is more than a specified value.
    It is effective in NMEA(with GGA sentence) and RBT-3000 and i-Blue series(with HDOP, NSAT)
    and BT-Q1000(with HDOP, NSAT) of log.
    A setting dialogue opens at the time of a check.

  5)Reduce.
    If it checks, Data is outputted when it passes more than designated time or
    beyond specification distance is moved.
    A setting dialogue opens at the time of a check.

  6)Output in local time.
    UTC is converted at local time and it outputs it to "Point note".

  7)Output range limitting.
    The range of output data can be specified at time when checking it.
    Because the "Output range" dialog for the output range setting is displayed when the
    data file reading is completed, time is input directly to "Start Time" and "Final Time"
    and the "OK" button is clicked.

    Or, when the line for which ListView hopes is clicked, the value of "Start Time" is Updated.
    When the line for which ListView hopes after clicking the "View Final data" button is
    clicked, the value of "Final Time" is updated.

    The page can move back and forth by clicking "Prev" and "Next" button.

    The "Block Selector" dialog opens previously when data is divided.
    When the check box is made Off, the block is not output.
    Because the "Output range" dialog opens when a target line is clicked, the range of
    the output in the block can be set.
      "Reset"   button: All blocks are checked, and all the points are output.
      "All Off" button: The check on all blocks is made Off.

      Note)The part that exceeds 23:59:59.9 with UTC cannot be specified because there is
           no date information when there is no RMC sentence in the NMEA input.

  8)Output File type.
     KML:  It outputs by the Keyhole Markup Language form.
     KMZ:  It outputs by extension name .kmz by compressing KML in ZIP.
     GPX:  It outputs by the GPS eXchange Format.
     NMEA: Output a file of an NMEA format.
     CSV:  File of CSV is output (Input from the CSV file is improper).

  9)Track & Placemark.
    It is effective only to the output of KML or KMZ form.
    Random color:   Line color of tracks is decided at random.
    Without indent: The line head tab of KML, KMZ and the GPX file is not output.
    Visible only:   Placemark of non-display is not output when checking it.
    3D:  The altitude is applied to tracks.
         It displays it in the ground level when not checking it.
      A setting dialog opens when checking it.
      View point.
        Tilt:    Angle in degrees (0:directly above, 90:viewing along the horizon).
                 Values range from 0 to 90 degrees.
        Clump to ground:  
           Track:     Tracks are fixed to the ground.
           Placemark: Placemark are fixed to the ground.
        Range:
           At "Auto setting" check on.
               The distance to the view point is set automatically 
               (The magnification can be specified by X. Default value is 1.2 ).
           At "Auto setting" check off.
               Distance in meters from the point specified by the LookAt position.
        Heading:
           At "Auto setting" check on.
               The direction is set to become it as much as possible at orthogonally with
               tracks automatically.
               North: It sets it within the range of -90..0..90 degrees.
               East:  It sets it within the range of 0..90..180 degrees.
               South; It sets it within the range of 90..+-180..-90 degrees.
               West:  It sets it within the range of -180..-90..0 degrees.
           At "Auto setting" check off.
               Direction in degrees (0: North).
               Values range from 0 to 360 or -180 to 180 degrees.
        Position:
           At "Auto setting" check on.
               The View position is set automatically.
               Start:   Starting point.
               Halfway: Halfway point.
               Final:   Final point.
           At "Auto setting" check off.
               The latitude longitude and Altitude are input by the numerical value.
               For 135 degrees 30 minutes 30 seconds of east longitude
                 135∞30'30"
                 135 30 30 E
                 135.508333
               It is possible to input it as above.
               The input value is converted into the decimal number.
      Extrude.
        Track extrude:  Extruded LineString looks like a fence.
        Point extrude:  Extends the line down to the ground.
      Altitude mode.
        Clamp to ground:    Tracks are fixed to surface of the earth.
        Relative to ground: Tracks are displayed on relative ground from surface of the earth.
                            Note) The altitude data as for the negative part does not
                                  indicate tracks.
        Absolute:           Tracks are displayed in the sea level altitude.
                            Note) As for the part where the Altitude data is lower than 
                                  surface of the earth, tracks are not displayed.
                                  Please use it for the data such as the glider or aircraft.
      Altitude is replaced speed.
        Replace:      Altitude is replaced at the speed when checking it.
        Coefficient:  Coefficient of transformation to Altitude. m/(km/h)
        Offset:       Value added to Altitude (m)
                        Altitude = Spped * Multiplying factor + Offset

      Summary display.
        T: Tilt.
        R: Range(Auto or m).
        H: Heading(N,E,S,W or degree).
        AP: Auto position, MP: Manual position.
           (St): Start point.
           (Hw): Halfway point.
           (Fin): Final point.
        TE: Track extrude.
        PE: Point extrude.
        CG: Clamp to ground, RG: Relative to ground, Abs: Absolute.
        Rp: Altitude is replaced speed.

      Refer to: http://homepage2.nifty.com/k8/gps/tracksample.htm

    Track:   Track is output (Line string).
    Point:   Point is output (Place mark).
     Balloon: When Placemark is clicked, Placemark note is displayed with the information balloon.
              The dialog for the Point name selection of Placemark note is opened when keeping 
              effective.
     TimeStamp: The TimeStamp element is output to Placemark.
                It is necessary for the Geo tagging in the photograph etc.
    Line width: Line width of tracks is specified (0 to 4 is recommended).
                With a PC, it can be ignored.
    Alpha:   Opacity of tracks is specified (0 to 255).
    Color:   Line color of tracks is specified by clicking.
    Speed:   Set three kinds of border speed
             (Speed is inputted rightward in ascending order).
             When the text at the speed unit is clicked, it is revokable in order of
             Km/h -> mph -> kt.
    Logo:    "External Icon selecter" form opens when clicking.
             An external icon and the logo mark can be set.
               Xpos: 1=Right edge, 0=Left end (0 to 1).
               Ypos: 1=Top,        0=Bottom (0 to 1).
               Scale: Ratio of screen (0 to 1). -1= Original size.
             Note) Only ASCII character can use it for the image file name,
                   and only the PNG format can be used.
                   When the file name is a blank, the logo is not output ("Logo" is displayed 
                   by the lower case).
    Visible: A check will display the point by a default.
    Int. Icon / Ext. Icon:
             The icon source is switched to an internal icon and an external icon when clicking.
             The icon can be changed by clicking an individual icon image.
    POI1,2.  A check will display the Interest point by a default
             The display item can be specified by the configuration file.
    Start:   Displays it with the icon that specifies the first point.
    End:     Displays it with the icon that specifies the end point.
    Scale:   The display size of each icon is specified by the coefficient ( Default is 1.0 ).

 10)Datetime format.
    The format of date and time in "Point note" is specified.
    When starting, it acquires it from OS automatically when "Auto" is checked.

    Format character "z" is used to display less than second.
        Ex) hh:mm:ss.zzz     Under a second can be specified to 3 digits.
    When a termination by ".", the zero suppression display of under a second is performed.
        Ex) h:mm:ss.
               9:12:34.000 -> 9:12:34
               9:12:34:030 -> 9:12:34.03
               9:12:34:200 -> 9:12:24.2

 11)Localtime - UTC.
    The time difference at UTC and Local-time is specified (09:00:00 in Japan).
    When starting, it acquires it from OS automatically when "Auto" is checked.

 12)Geoid.
    The geoid correction method is set.
    The dialog for the setting pop up when the checkbox is checked.
    When the "OK" button is clicked, the setting is applied.

    Geoid model
      Fixed value:       It corrects it by a fixed value regardless of the position.
      EGM2008 2.5'x2.5': It corrects it by using 2.5'X2.5' grid data of NGA.
      EGM2008 1'x1':     It corrects it by using 1.0'X1.0' grid data of NGA.
      GSIGEO 2000:       It corrects it by using 1.0'X1.5' grid data of Geographical Survey Institute.
                         When it selects first time, it takes time to convert it into the binary data.
      Custom Geoid:      It corrects it by using the geoid file that does the clip by the CustomGeoid utility.

    Processing method.
      CSV and NMEA input including Geoid:
         Output_altitude <- GPS_altitude +  GPS_geoid - Compute_Geoid
         Output_geoid    <- Compute_Geoid
      Geoid is not included in the input:
         Output_altitude <- GPS_altitude - Compute_Geoid

    Geoid check.
      The geoid height can be confirmed by clicking the "Check" button.
      The latitude longitude can be input by the following format.
        37 48 51.28 S,  -37 48 51.28,  -37.814244444,  37∞48'51.28"S,  -37∞48'51.28"

    Note 1) The altitude becomes illegal when applying to the file in the sea level altitudes (When there is
            no geoid input).
    Note 2) The Geoid correction is not applied for .tks .tk1 .tk2 .tk3 the extension name of the input file.

    Reference)
      EGM2008 2.5'x2.5'
        Geoid model data of National Geospatial-Intelligence Agency (NGA).
        Grid data of latitude longitude of 2.5 minutes (149,368,328Bytes).
        The all earth data is contained(Latitude: -90∞ to 90∞, Longitude: 0∞ to 359∞57'30").
        Spline interpolation of interpolation (The vicinity of two poles applies the bi-linear interpolation).
      EGM2008 1'x1'
        Geoid model data of National Geospatial-Intelligence Agency (NGA).
        Grid data of latitude longitude of 1.0 minutes (1,382,324,722Bytes).
        The all earth data is contained(Latitude: -90∞ to 90∞, Longitude: 0∞ to 359∞59'00").
        Spline interpolation of interpolation(The vicinity of two poles applies the bi-linear interpolation).
        Because the difference with EGM2008 2.5'x2.5' is about less than 3.5mm, 2.5'x2.5' is usually enough.
      GSIGEO 2000
        Geoid model data of Geographical Survey Institute (in Japan).
        Grid data of longitude 1.5 minute and latitude 1.0 minute (19,670,776Bytes).
        Latitude: 20∞ to 50∞ and longitudes: 120∞ to 150∞.
        Hokkaido, Honshu, Shikoku, Kyushu and neighboring waters, and a part of solitary island is contained.
        Bi-linear interpolation of interpolation (Spline interpolation is also possible by option).
        Difference with EGM2008
          Mean value about 0.266m of difference.
          The maximum value about 2.7m of difference (Tarama island northwest sea).
          The maximum difference about -0.61m in land in Hokkaido, Honshu, Shikoku, Kyushu(Cape Nosappu).
          The maximum difference about 1.51m in solitary island land (Okinoerabu island).
          The difference in Tokyo Station is about 0.216m.

 13)Ground level.
    The surface of the earth altitude is specified.
    The surface of the earth altitude is subtracted from the height of the data source 
    when "Apply" is checked and it displays it in the height of "Placemark note".
    Note) Because it is not possible to correspond to the change in the surface of the 
          earth altitude, it is not suitable for the large area data.

 14)Placemark note (KML/KMZ).
    It is effective only to the output of KML or KMZ form.
    The output items of the Placemark annotation is specified.
      No.   : Sequence number is output.
      Date  : Date is output.
      Time  : Time is output.
      Long. : Longitude is output.
      Lat.  : Latitude is output.
      Speed : Speed is output (Unit chooses it with an "Track - Speed" option).
      Alt.  : Altitude is output.
      Hdop  : HDOP is output.
      Nsat  : Number of use satellites is output.
      Temp    : Temperature is output (Only WSG-1000).
                Log output range: -10 to 52 degrees (2 degree steps).
      Pressure: Barometric pressure is output (Only WSG-1000).
                Log output range: 589 to 1100hPa (1hPa step).
      Pressure Alt: Pressure Altitude (Only NMEA of WSG-1000).
      Voice : Voice file name is output (Only V-900, VGPS-900).

 15)CSV option (CSV)
    It is effective only to the output of CSV form.
      Index    : Sequence number is output.
      Date+Time: Date and time are output to item "TIME".
      S/N,E/W  : Positive and negative in the latitude and longitude is output to the
                 separating item.
      Geoid    : Geoid value is output.

4.Command line option.
  The batch conversion of the file can be done by specifying two or more NMEA file and
  configuration file NME2KMZ.ini.
  It is finished automatically when include /Q in a command-line.
    Ex.) NMEA2KMZ 06-08-01.nmea 06-08-10.nmea /Q

  When blank is included in path or file name, it is necessary to surround with the
  double quotation mark.
    Ex.) NMEA2KMZ "C:\Documents and Settings\User\06-08-01.nmea"

5.Drag & drop.
  The batch conversion of the file of two or more input file and configuration file
  NME2KMZ.ini can be done to the execution file icon or the form by dragging it.

6.Configuration file.
  The options setting when ending is preserved in NMEA2KMZ.ini of the same to execution 
  file folder.
  Two or more configuration files are preserved and it is possible to select it with 
  the command line or the drug & drop.
  When the folder with the configuration file is read-only, it copies onto folder 
  %APPDATA%\NMEA2KMZ\ and it uses it.
  %APPDATA% is a folder displayed to input by the DOS prompt as "echo %APPDATA%" <Enter>.

 [Option] section.
   Can appoint a Log file filter of RoyalTek RBT-3000, Wintec WBT-200, WBT-201, 
   i-Blue series and HOLUX M-241 in a [Option] section.
   Setting of default:
     WBTmask=*.tks
     RBTmask=*.txt
     iBluemask=*.csv
     Holuxmask=*.trl
   Ex)
     WBTmask=read_at_*.tks

   Accel_g: The limit acceleration at the speed calculation can be specified
            ( 1.0 = 9.8m/S^2 ).

   WPL_Prefix: The point name prefix of the WPL sentence of NMEA to POI1.
   WPV_Prefix: The point name prefix of the WPL sentence of NMEA to POI2.

 [CSVtag] section.
   Interest:  Character of the RCR(TAG) item corresponding to POI1 (default: "B").
   Interest2: Character of the RCR(TAG) item corresponding to POI2 (default: "V").

 [CSVitem] section.
   The item name of the CSV input file can be specified.
   Two or more names can be specified by delimiting by comma (,) .
     RCR      : Record method(Time, Button, Voice).
     Date     : Date.
     Time     : Time.
     Valid    : GPS quality indication.
     Latitude : Latitude.
     NS       : North/South.
     Longitude: Longitude.
     EW       : East/West.
     Height   : Altitude.
     Speed    : Speed.
     HDOP     : HDOP.
     Nsat     : Number of satellites (Used/View).
     Temp     : Temperature.
     Barom    : Barometric pressure.
     PAlt     : Pressure Altitude.
     Voice    : Voice file name.
     Geoid    : Geoide height.

 [Separator] section.
   The separator of the output file name at time of the date can be specified.
     DateSep: The separator at the Date (Default is "-").
     TimeSep: The separator at the Time (Default is "-").
     DateTimeSep: Separator at date and time (Default is "_").
       Note) The numeric and a some symbol cannot be used ( \/,;:*?"<>| 0123456789 ).

 [Font] section.
   The display font is specified.

   Default value in Japanese locale.
     Charset=128
     FontName=MS PGothic
     FontSize=9
     DegChar=Åã

   Initial value of other locales.
     Charset=0
     FontName=Arial
     FontSize=8
     DegChar=∞

   DegChar: Degree symbol.
   Please note excess to the display area according to the font and the size.

 [Icon] section.
    When "InternalImage=" is added, the bitmap(.BMP) file for the internal icon selection 
    can be specified.
    The bitmap size is 512x512 pixel, and 256 icons of 32x32 pixel are contained.
    It is not necessary to add it usually.

 [Note] section.
   The number of digits below the decimal point of the Note of placemark is 
   specified.
     LatLonDecimal: Number of digits below decimal point in Latitude/Longitude
                    (4 to 8 digits).
     AltDecimal:    Number of digits below decimal point in Altitude (1 to 8 digits).
     SpeedDecimal:  Number of digits below decimal point at Speed (1 to 8 digits)..

 [NMEAopt] section.
   IgnoreSpace : After space in the NMEA sentence is deleted, it analyzes it for "1".
                 It analyzes it as it is for "0".

 [KMLKMZopt] section.
   IconToKMZ : An external icon is built into the KMZ file at "1".
               It is assumed only the KML file for "0".

 [CSVopt],[KMLKMZopt],[GPXopt],[NMEAopt] section.
   The number of digits below the decimal point of various data is specified.
     LatLonDecimal: Number of digits below decimal point in Latitude/Longitude
                    (4 to 8 digits).
     AltDecimal:    Number of digits below decimal point in Altitude (1 to 8 digits).
     SpeedDecimal:  Number of digits below decimal point at Speed (1 to 8 digits).
                    ([KMLKMZopt] and [GPXopt] are excluded).

 [CSV_Info] section.
   The GPS name individually processed and the CSV item for the distinction are described
   (The user can add it).
   Format: GPSname=Unique CSV item
   Ex)
      Wintec=Order,Date Created,Bearing,Elevation,Distance from Start,Distance from Last
      V-900, VGPS-900=TAG,LATITUDE N/S,LONGITUDE E/W,VOX
      M-241=M-241

 [CSV_Option] section.
   The content of processing to the GPS name is specified (The user can add it).
   GPS name "Default" is applied to all GPS outside specification.
   Format: GPSname=Param1,Param2,Param3,Pram4,Param5

          Param1: Date time.
            0: UTC.
            1: Local time.
          Param2: Altitude.
            0: Indetermination.
            1: Mean sea level (Geoid setting is ignored).
          Param3: Date update error.
            0: No error.
            1: With error.
          Param4: Speed unit.
            0: Km/h.
            1: mph.
            2: knot.
          Param5: Altitude unit.
            0: m.
            1: feet.
   Ex)
      Default=1,0,0
      Wintec=1,1,0
      V-900, VGPS-900=0,1,1
      M-241=0,1,0

 [Geoid] section.
   GeoidPath:  Path with the geoid grid data is specified.
               It is considered the same to execution file folder in case of emptily.
   GeoidModel: Geoid model who has been selected.
   Digit:      Digit number below geoid decimal point of NMEA output.
   PostFix:    The end of the file name in which the geoid correction is excluded is specified.
   GeoidValue: Fixed geoid value (m).
   Apply:      The geoid correction is executed by one.

 [EGM2008_25],[EGM2008_10],[GSI2000] section.
   fname: File name of geoid model.
   nrows: Number of input data of directions of Y.
   ncols: Number of input data of directions of X.
   glamn: Latitude in the south end.
   glomn: Westernmost longitude.
   dgla:  Data step of latitude (degree).
   dglo:  Data step in longitude (degree).
   nlat:  Number of effective data of directions of latitude.
   nlon:  Number of effective data of directions of longitude.
   PrePad: Number of invalid data of longitude heads.
   Spline: The spline interpolation is used by one (Only GSI2000).

 [PG-S1] section.
   It sets it concerning the barometer of Hanwha Pocket GPS S1 (PG-S1).
   UseBarometer:    The barometric pressure and the pressure altitude are output by "1"
                    (Turnoff by "0").
   BarometerOffset: The offset value for the barometric pressure correction is set
                    (Unit is hPa).
   Fahrenheit:      "1" when temperature is input by Fahrenheit.

7.About the NMEA data.
  Two sentences of GGA and RMC sentence are used.
  When there is not a RMC sentence, cannot output Date.
  In this case speed calculates it from distance and an elapsed time.
  When there is not a GGA sentence, cannot output Altitude.

8.About the CSV file format.
  It is a form in the first line since the item name and the second line to contain data
  (The small and capital letter becomes the same result).

  Effective item name and content.
  rcr :         "B" is interest point.
  date :        Date (UTC yyyy/mm/dd).
  time :        Time (UTC hh:mm:ss or hh:mm:ss.sss).
  valid :       "no fix" or "0" is non-determines position.
  lat,
  latitude :    Latitude (dd.dddddd).
  n/s :         "N" or "S" (If it is sign addition Latitude, it is unnecessary).
  lon,
  long,
  longitude :   Longitude (ddd.dddddd).
  e/w :         "E" or "W" (If it is sign addition Longitude, it is unnecessary).
  height :      Altitude (m).
  speed :       Speed (Km/h).
  hdop :        HDOP.
  nsat (used/view),
  nsat,
  used sat :    Number of use satellites.
  temp :        Temperature.
  barom :       Barometric pressure.
  palt :        Pressure Altitude.
  vox:          Voice file name.
  geoid:        Geoid height.

  1)The item of the other than above is ignored.
  2)Minimum necessary items are "time", "latitude", "longitude".
  3)When there are no "Date" items, the contents of "time" can be made "yyyy/mm/dd hh:mm:ss".
  4)Each item is permitted in any order.

Example of CSV data:
INDEX,RCR,DATE,TIME,VALID,LATITUDE,N/S,LONGITUDE,E/W,HEIGHT,SPEED,HDOP,NSAT (USED/VIEW),
1,T,2008/03/14,10:17:51,No fix,35.508158,N,139.614472,E,150.000 M,0.000 km/h,99.99,0(9),
2,B,2008/03/14,10:17:52,SPS,35.365336,N,139.530571,E,150.000 M,28.188 km/h,2.23,3(9),
3,T,2008/03/14,10:17:54,SPS,35.365038,N,139.530461,E,150.000 M,34.831 km/h,2.23,3(9),

9.Troubleshooting

  1)A message of "No data" is displayed, and a file is not make.
    a)The possibility that non-fix is in a state has NMEA data.
      Please try to exclude a check of check box "Use Fix-data only".
    b)Mask is effective and "HDOP" is less than 1.0 or "Satelites used" is more than 12.

  2)File making to the under "Program Files" folder is not possible in Windows vista.
    Please execute it after copying the input file onto another folder.

  3)The track icon is not displayed.
    When an external icon is used by the KML form, the icon file is necessary for the 
    same folder.
    Because the KMZ form contains the icon file, it is possible to distribute it with 
    a single file ( Exclude it in the [KMLKMZopt] section of the configuration file in 
    case of "IconToKMZ=0" ).

  4)Tracks are not displayed in 3D mode.
    When altitude data of GPS is lower than that of earth's surface, tracks are not
    displayed.
    Please make 3D mode Off about the ground level log data such as on foot.

  5)Warning sounds it in the click of ListView.
    Please refer to the following page.
      MSKnowledgeBase
      http://support.microsoft.com/kb/944150/en-us/

  6)3D is not displayed to tracks and the Please make.
    Please confirm the setting of 3D setting dialog.
    Please confirm whether neither "Track Clamp to ground" nor "Placemark Clamp to ground"
    of "View point" are checked.
    Please confirm whether "Clamp to ground" is checked by "Altitude mode".

  7)The height display of 3D mode is illegal.
    Please confirm whether "Replace" is checked by "Altitude is replaced at speed" of 
    3D setting dialog.

  8)Binary file "gsigeome.ver4.dat" cannot be make.
    Please right-click in the execution icon and start by the administrative right when 
    you put the data file since Windows Vista under "Program files" (It only first time).

  9)The place mark icon is not displayed.
    When TimeStamp is output, it is necessary to set the beginning time and the end time
    by the slider of Google Earth at DateTime.

10. One-point advice.

 1)Procedure when two or more log files are join on and it outputs it to KML/KMZ.
   Files are bind by the DOS command of the command prompt.

   Start and terminate of command prompt.
     Start:  Start -> All Programs -> Accessories -> Command Prompt,
             or "command[Enter]" is input with Start -> Run.
     Movement of current drive:  It moves to "D" drive by "D:[Enter]".
     Movement of folder:         It moves to the "\temp" folder by "CD \temp[Enter]".
     terminate:                  It terminate by "exit[Enter]".

    1) For ". trl" log file of M-241 (".TES" file of WBT-202 is also similar).
       Because it is a binary file without the header, it is possible to join on by the COPY
       command of the command prompt.
       Ex) When "a.trl", "b.trl", and "c.trl" are join on and "t.trl" is made.
           copy /B a.trl+b.trl+c.trl t.trl[Enter]

    2) For log files other than M-241.
       After it converts it into ".csv" or ".nmea" with NMEA2KMZ once, it join on by the COPY
       command of the command prompt.
       Ex) When "a.csv" and "b.csv" are join on and "t.csv" is made.
           copy a.csv+b.csv t.csv[Enter]
   
    KML/KMZ is made from the combined log files with NMEA2KMZ.
    Please enlarge enough at this time "Split Time" of "Option", and prevent division in 
    contradiction to the mind.

 2) About the external icon file.
    The size uses the file of the PNG format of 32x32 pixel.
    It arranges it in either of images at about 16x16 pixel at an upper and lower 
    right and left and center in this usually.
    The transparence display cannot be done in BMP and the Jpeg format.
    Only the PNG format can be used for the Logo image.
    When making it with Adobe PhotoShop:
      After it draws to a upper layer, and the background layer is made non-display,
      it saves by the PNG format.
    The transparent color becomes a pixel at the bottom of the left end of the image.
    Note) Only ASCII code can be used for the image file name (Multibyte character 
          cannot be handled).


In compiler used
    CodeGear Delphi 2007 Professional(Delphi for Win32)   Borland Software Corp.

Component used
    "PNG Delphi version 1.56" is used for reading the PNG image.


Release note.
  * This application is the free software.
  * This application is redistributable, but please distribute it including an execute
    file and a document.
  * The author takes no responsibility to any losses and obstacles which were produced
    by use or distribution of this application.


Version history.

 Ver2.20
   1. Bug fix of NMEA to KML and KMZ.
      The bug when NMEA without RMC was input with Start icon Off was corrected.

 Ver2.19
   1. Course was added to the RMC sentence of the NMEA output.
   2. Kilo was corrected to the lower-case.

 Ver2.18
   1. The size of the icon was able to be specified by the coefficient.

 Ver2.17
   1. The output timing of the barometric altimeter of Hanwha Pocket GPS S1 (PG-S1)
      was corrected.

 Ver2.16
   1. Bug fix of pressure altitude processing of Hanwha Pocket GPS S1 (PG-S1).
      It was corrected that the altitude was corresponding to a specified value.

 Ver2.15
   1. The temperature correction was added to the pressure altitude processing of
      Hanwha Pocket GPS S1 (PG-S1).

 Ver2.14 Jul. 2010
   1. Barometric altimeter processing of Hanwha Pocket GPS S1 (PG-S1) was added.

 Ver2.13 Jun. 2010
   1. It corresponded to POI of Hanwha Pocket GPS S1 (PG-S1).

 Ver2.12 Dec. 2009
   1. The size of the Custom geoid file was checked.

 Ver2.11 Dec. 2009
   1. It corresponded to the Custom geoid file.

 Ver2.10 Nov. 2009
   1. The CSV file of Canmore Phototracker is processed.

 Ver2.09 Oct. 2009
   1. It corresponded to reading log file (.nma) of TripMate850.

 Ver2.08 Oct. 2009
   1. "Z" was added to the end of the time of <TimeStamp> element.
   2. It corresponded to a consecutive $GPWPL sentence when NMEA was input.
   3. When NMEA and CSV were input, POI output MASK disregarding it.
   4. POI output the Reduce setting disregarding it.

 Ver2.07 Oct. 2009
   1. An optional output of <TimeStamp> element was added to the KML/KMZ.
   2. It was fixed that track information had been included in the KML/KMZ without Track.

 Ver2.06 Oct. 2009
   1. The ".TES" file of Wintec WBT-202 is treatable.
   2. The converted ".tk2" file of Wintec WBT-202 is treatable.
      It doesn't make to the error even if there is no GPS type name and the case with
      the log type is disregarded.

 Ver2.05 Sep. 2009
   1. It supported ".trl" file with the speed of M-241 firmware Ver1.13.

 Ver2.04 Sep. 2009
   1. The open of the geoid-model file by other programs simultaneously was permitted.
   2. Geoid value of NMEA sentences of more than +-150m when to ignore.

 Ver2.03 Aug. 2009
   1. Corresponded to the Geoid item of the CSV file.
   2. The bug when the geoid was a manual value was fixed.

 Ver2.02 Aug. 20009
   1. Geoid correction of NMEA data and conversion from WSG84 ellipsoid height of the CSV file to
      the sea level altitude was corrected corresponding to the latitude longitude.
      It deals with the geoid model of Geographical Survey Institute(Japan) and National Geospatial-Intelligence Agency.
   2. "UTC DATE" and "UTC TIME" were added to Date and Time of the [CSVitem] section.

 Ver2.01 Mar. 2009
   1. Google Earth internal icon was output with URL (<X><Y><W> is abolished).
   2. The display of Date and Time of Balloon was separated.

 Ver2.00 Feb. 2009
   1. Point name at the Balloon mode was able to be selected.
   2. The Speed icon was not displayed when there were POI1 or POI2.
   3. When the position or the scale of Logo was illegal, it set it to the default value.

 Ver1.59 Feb. 2009
   1. The bug from which the height of LineString had been doubly subtracted when Geoid was 
      applied to the KML/KMZ output was corrected.
   2. The bug that an external icon of "Speed 1" is not built into the KMZ file was corrected.

 Ver1.58 Feb. 2009
   1. The bug when beginning and the end point included the interest points was corrected.
   2. "Logo" display of the screen was displayed by the capital letter in the Logo output mode.

 Ver1.57 Feb. 2009
   1. The specification of "Ground level" mode was changed.
      Only the altitude of "Placemark note" was made to change.
   2. The Logo display function was added.

 Ver1.56 Feb. 2009
   1. The bug when the icon file was added to the KMZ file was corrected.
   2. The option to read the internal icon list image was added.

 Ver1.55 Feb. 2009
   1. The type of CSV was able to be specified by the configuration file.
   2. The option of the Voice file name output was added to "Place note".
   3. The display of NSEW was added to the latitude longitude display of "Output range" form.
   4. The update defect data of the date of "Columbus V-900" was disregarded.
   5. The icon of the beginning point and the end point was able to be specified.
   6. The external file was able to be used for the Placemark icon.
   7. The function to convert height into the ground altitude was added.

 Ver1.54 Jan. 2009
   1. Added the option which displayed Placemark note with an information balloon
      when clicked Placemark.
   2. Replaced the order of the latitude and longitude of "Placemark note".
   3. When the Geoid specification was disregarded, the message was displayed on the 
      Memo screen.
   4. Option to disregard Space(0x20) in the NMEA sentence was added to the
      configuration file.

 Ver1.53 Jan. 2009
   1. The icon display was added to the list view of "Output Range" screen.
   2. Page feed button was added to "Output Range" screen.

 Ver1.52 Dec. 2008
   1. Added an option in ignore of dead reckoning data.
   2. Revised that the last data were ignored in the case of GGA only or RMC only.
   3. It was made not to output the icon information which is not used for KML/KMZ.

 Ver1.51 Nov. 2008
   1. Bug fix a judgment of N/S, E/W of the latitude longitude of the CSV input in Ver1.50.

 Ver1.50 Nov. 2008
   1. The CSV data of Columbus V-900 is processible.
   2. Added "VALID" to the item of the CSV output.
   3. Expanded POI to two kinds.
   4. Able to define a character of RCR(TAG) in a configuration file.

 Ver1.49 Oct. 2008
   1. When the extension name of the input file was .tks .tk1 .tk2 .tk3,
      the Geoid specification was not applied.
   2. When the GGA sentence contained Geoid in the case of the NMEA input,
      the Geoid specification was not applied.
   3. The number of digits below the decimal point in the Latitude/Longitude, Altitude
      and Speed of the output file was able to be specified by the configuration file.
   4. Other detail was corrected.

 Ver1.48 Aug. 2008
   1. When the speed was not included in the RMC sentence of the NMEA input, the speed 
      was obtain by the calculation.
   2. The speed calculation when time did not change, returned the speed immediately before.

 Ver1.47 Jul. 2008
   1. Automatic setting function of 3D Heading was added.
   2. The magnification was able to be set to AutoRange of 3D.
   3. The display of the number of data points was added to the "Block Selector" dialog.

 Ver1.46 Jul. 2008
   1. It was corrected might not be able to select the first point of Block by "Output Rane"
      dialog (Only when Localtime offset was negative).

 Ver1.45 Jul. 2008
   1. It was corrected that the speed of the CSV input was illegal.
   2. It fitted the unit of the speed of the "Output Range" dialog to the setting of the
      main form.
   3. When it is a Japanese locale and DegChar is "∞", it changes to "Åã".

 Ver1.44 Jul. 2008
   1. The Halfway of 3D view point was brought close to the center of the moving range.
   2. The value of the "Range" automatic setting of 3D was calculated from the moving range.
   3. When the locale was Japan, an initial value of the font was changed to "MS PGothic".
   4. The average speed was added to "description" of the KML/KMZ output.
   5. All parameters of 3D Option were maintained.
   6. Other detail was corrected.

 Ver1.43 Jul. 2008
   1. The final time was able to be added to the output file name.
   2. Space(\S) was able to be specified for the separator of the output file name.
   3. The start time and the finish time were able to be specified at every the block.
   4. The unit of the speed of the CSV I/O was fixed to km/h.
   5. The output condition setting dialog of 3D mode was added.
   6. It was made to display by converting the speed into the altitude in 3D mode.

 Ver1.42 Jun. 2008
   1. The range of output data was able to be specified at time.
   2. The display font was able to be specified by the configuration file.
   3. The separator of the output file name at time of the date was able to be specified
      by the configuration file.
   4. The fault in the case of RMC or GGA sentence only was corrected in the NMAE input.

 Ver1.41 Jun. 2008
   1. Output of Track and Point was able to be On/Off (KML/KMZ).
   2. Icon was changed.

 Ver1.40 Jun. 2008
   1. Altitude was able to be applied to tracks.
   2. Dialog was displayed at the center of Form.

 Ver1.39 May. 2008
   1. The $IISMD sentence was accepted to the NMEA input.
   2. Barometric pressure, temperature and pressure altitude were accepted to the CSV input.
   3. The item name of the CSV input was able to be specified by the configuration file.
   4. Hint display was corrected.

 Ver1.38 May. 2008
   1. The output of CSV was added.
   2. Temperature and barometric pressure were able to be output to the point note of
      KML/KMZ(Only WSG-1000).
      Barometric pressure: -10 to 52 degrees (2 degree steps).
      Temperature: 589 to 1100hPa (1hPa step).

 Ver1.37 May. 2008
   1. Corresponded to a numeric form of the "Valid" item of the CSV file.
   2. The altitude from WGS84 ellipsoidal was converted into the sea level altitude by
      adding the specification of Geoid.
   3. The comment on the distance and the speed of KML/KMZ was corrected according to
      km/h, mph, and kt of Speed.
   4. Corrected that the value of "Moving Distance" of Reduce to the km/h, mph, and kt
      changes of Speed did not become illegal.

 Ver1.36 May. 2008
   1. Corresponded to the tk1, tk2, tk3 file of Wintec WSG-1000.
   2. Corresponded to the CSV file reading of Wintec.
   3. Detection of reversing the time of the CSV file was judged by the reversal for 60 seconds
      or more (For the mis-detection prevention by the log of every 0.2 seconds or less).
   4. Delimiter between Date and Time of the output file name was changed from "_" to "-".

 Ver1.35 Mar. 2008
   1. Regarded as "OK" by "Enter" key in Reduction form and Mask form, and was made to 
      regard it as "Cancel" by "ESC" key.
   2. When the number of use satellites is invalid in the GGA sentence of NMEA, it output 4,
      when HDOP is invalid, it tried to output 1.5.
   3. NULL was output to "True Course" of the RMC sentence of NMEA.
   4. The system error message was returned from Japanese to English.

 Ver1.34 Mar. 2003
   1. The ZIP compression was built in the execution file and external DLL became unnecessary.
   2. Added the option which deleted a line head TAB from a KML, KMZ and GPX output file.
   3. HDOP and Nsat can have been displayed in the Placemark comment of KML and KMZ.
   4. The error of KML and KMZ output when all Placemark was made off was corrected.
   5. ".LOG" was added to the extension name of the NMEA file.

 Ver1.33 Mar. 2003
   1. The mask function in HDOP and NSAT was added to reading the log of the i-Blue series,
      BT-Q1000, RBT-3000 and NMEA.
   2. A setting value of the thinning out condition and the HDOP and NSAT mask was displayed
      in the checkbox caption.
   3. Reduce and Mask dialogue were displayed at the center of the main form.
   4. The trouble of the command line specification of the configuration file was corrected.
   5. Three kinds "Nsat(used/view)", "Nsat", and "Used sat" were admitted in finding the 
      number of use satellites of CSV files.
   6. In addition correction of detail.

 Ver1.32 Mar. 2003
   1. The data of "90.0N 0.0E" of the CSV file was disregarded.
   2. The track icon was renewed at the drug of the configuration file.
   3. The option not to output Placemark of non-display was added (KML and KMZ output).

 Ver1.31 Mar. 2008
   1. The trouble of the processing when the log time reversed was corrected
      (When dividing an output file by an end of a CSV file, processing is prohibited).
   2. The interruption message by the escape key was displayed.
   3. The exception handling was enhanced.

 Ver1.30 Mar. 2008
   1. The trouble of the processing when the log time reversed was corrected
      (When the end of a CSV file is "No Fix").

 Ver1.29 Mar. 2008
   1. corresponded to the case where the log time of the  BT-Q100 and i-Blue series was reversed.
      The first log is connected with the log data of the end and it makes it continuously.
   2. The unit of the elapsed time for thinning out was changed from "Minute" to " Second".
   3. The file of two or more output forms can have been output at the same time.

 Ver1.28 Feb. 2008
   1. The processing of the parameter of E/W in the longitude of the GGA sentence was corrected.

 Ver1.27 Feb. 2008
   1. Corrected that a minus sign was extra output by the south latitude and the 
      west longitude of the NMEA output.

 Ver1.26 Feb. 2008
   1. The division output in lack time was also made effective at the time of logfile 
      reading of M-241.
   2. Resizing processing of the MEMO form was corrected.
   3. The Track group box assumed that a change was possible only in KMZ and KML output.

 Ver1.25 Jan. 2008
   1. The output of the GPX file was added.
   2. The mistake of the distance calculation with the interest point was corrected.

 Ver1.24 Jan. 2008
   1. The Log file conversion of HOLUX M-241 was added (*.trl).
   2. Measures when the configuration file was in a read-only folder were added.
   3. The caption of the GroupBox of Local-time was corrected.

 Ver1.23 Aug. 2007
   1. Some setting changes of the Interest icon revised that it was done wrong.

 Ver1.22 Aug. 2007
   1. Fault in case the delimiter of time is a period(".") was corrected.
   2. The code was optimized.

 Ver1.21 Aug. 2007
   1. Made to a zero suppression indication under of the second of a time display.
   2. Corresponded to Google Earth Ver4.2.0180.1134 (beta).

 Ver1.20 Aug. 2007
   1. Supported a tk2, tk3 format of WBT-201.
   2. The Interest point was disregarded with i-Blue747 and BT-Q1000 in the 
      longitude 0 degrees of latitude 90 degrees at non-fix.
   3. The format at the point note time can have been specified.
      The display at less than second became possible.

 Ver1.19 Jul. 2007
   1. The typing mistake of the status bar message was corrected.
   2. The processing of the command line option was corrected.
   3. The opacity of tracks of default was changed to 200.

 Ver1.18 Apr. 2007
   1. Time interval of acceleration restriction was expanded within 60 seconds within 
      5 seconds.
   2. Skip all zero record by logfile reading of WBT-200,201.
   3. When the time of the log reverses, report indication is performed.

 Ver1.17 Apr. 2007
   1. Speed calculation of Wintec WBT-200 and WBT-201 is also restricted by the 
      acceleration.

 Ver1.16 Apr. 2007
   1. The compiler was changed into Delphi 2007.
   2. The Log file conversion of Wintec WBT-201(G-Rays2) was added.

 Ver1.15 Mar. 2007
   1. The file name was made only into Time when there was no date information.
   2. It was made not to stop in the error of speed calculation.
   3. It enabled it to specify the point name prefix of the WPL sentence of NMEA 
      by the "NMEA2KMZ.ini" file.
   4. An initial value of the speed change limit at the speed calculation was changed 
      to the acceleration 0.5g.

 Ver1.14 Mar. 2007
   1. It was made to output Interest-Point to NMEA for a $GPWPL sentence.
   2. When speed was not contained in the log of i-Blue747, it was made to calculate 
      from move distance and time.
   3. Speed change was restricted with the acceleration of 3g at the time of speed 
      calculation.
      Configuration file "NMEA2KMZ.ini" [Option] Section It can change by "Accel_g".

 Ver1.13 Mar. 2007
   1. It was abolished to have cleared the RMC date by the GGA sentence reading.
      The change in the Date by the RMC sentence error and the skip at time were 
      prevented.

 Ver1.12 Mar. 2007
   1. The Log file conversion of Transystem i-Blue747 was added.
      Selection of the interest point was made possible.

 Ver1.11 Feb. 2007
   1. The ON/OFF specification of a First and Last track icon display was enabled.

 Ver1.10 Jan. 2007
   1. An extension name ".txt" But When there is not the log file of RBT-3000,
      It was made to retry as a NMEA file.
   2. It handling to Locales other than English and Japanese.
   3. The Track icon was extended to four kinds corresponding to speed.

 Ver1.09 Jan. 2007
   1. The client area of form was fixed.

 Ver1.08  Nov. 2006
   1. Even if the NMEA input file had an error, it stops and was made not to divide.

 Ver1.07  Oct. 2006
   1. Added NMEA to output file format.

 Ver1.06  Sep. 2006
   1. When command line option and the drug & drop doing, the fact that run-time error is 
      caused was corrected.

 Ver1.05  Sep. 2006
   1. Indicate 4 type everything simultaneously in when the selecting Track Icon.

 Ver1.04  Sep. 2006
   1. It supported Google Earth 4.0.2080 (beta).
   2. Enabled a reduce of the output.
   3. In addition correction of detail.

 Ver1.03  Sep. 2006
   1. Added Log file converter ability of RoyalTek WBT-200 ans RoyalTek RBT-3000.
   2. Added a report indication form.
   3. Added an output in movement distance and an elapsed time.
   4. When NMEA data did not have an RMC sentence, calculated speed from movement distance and 
      elapsed time.
   5. Added a function to divide an output file in the case of NMEA or RBT-300 by omission time.

 Ver1.02  Sep. 2006
   1. Coped with a change of icon image size.
   2. Unit of speed showed the case except km/h altitude in feet.

 Ver1.01  Sep. 2006
   1. Because the display of the point note when the latitude longitude was a 
      south latitude and a west longitude was illegal, it corrected.

 Ver1.00  Aug. 2006  First edition.
