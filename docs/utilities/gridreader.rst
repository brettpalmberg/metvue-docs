GridReader
==========

Usage
-----

.. code-block:: bash

    GridReader ((-inFile fileSpec (-outDir outputDirectory | -outFile outputFile))
               &| -controlFile file) [-type type] [-inUnits units] [-outUnits units]
               [-shg] [-dssA dssApart] [-dssB dssBpart] [-dssC dssCpart] [-dssF dssFpart]
               [-bTime time1] [-eTime time2] [-dTime timespan] [-shift timespan]
               [-title title]

Better Description
------------------

Read TINs or Grids in any MetVue-supported format and write to DSS or native MetVue TIN format

Options
-------

-inFile <fileSpec>
^^^^^^^^^^^^^^^^^^

Input filename. May use date masks and standard filemasks ``?`` and ``*`` to select more than one input file.

Two of the following options are required when using datemask strings to constrain InputFiles:

    #. :ref:`gridreader-btime`
    #. :ref:`gridreader-etime`
    #. :ref:`gridreader-dtime`

.. admonition:: Examples

    Single DSS file
        ``-inFile C:/mydata/MyData.dss``

    All *.rad* files in a outputDirectory
        ``-inFile C:/mydata/*.rad``

    All files that match a pattern for timespan with extension *.rad*
        ``-inFile C:/mydata/%yyyyMM%/%yyyyMMddHH%00z.rad``
        
        Note: Using ``00`` instead of ``mm`` for file minutes prevents an attempt 
        to find files for all minute values

    All files that match a pattern for timespan with any extension
        ``-inFile C:/mydata/%yyyyMM%/%yyyyMMddHH%00z.*``

    DSS files that match a pattern for any paths specified
        ``-inFile C:/mydata/%RadarData.%yyyyMM%.dss``

    Scan all
        ???

-controlFile <file>
^^^^^^^^^^^^^^^^^^^

Processing control file containing one or more argument blocks. Each block is separated by an empty line.
Options specified in the control file always take precidence over command-line options.
Required arguments for processing not specified in the control file are filled with command-line arguments.

.. code-block:: ini 

    # Example Control File Block 

    infile: inputFile.nc
    outfile: outputFile.nc
    btime: 06OCT1985,000000
    etime: 06OCT1985,010000

-outDir <outputDirectory>
^^^^^^^^^^^^^^^^^^^^^^^^^

Write output files to *outputDirectory* with filename based on input filename.
Can *not* be combined with option **-outFile**.

-outFile <outputFile>
^^^^^^^^^^^^^^^^^^^^^

Write output to *outputFile*. Can *not* be combined with option **-outdDir**. 
Images will be stored to DSS if *outputFile* is an existing DSS file or file extension is *.dss*.
Images will be stored in MetVue native TIN format if *outputFile* does not exist and file extension is not *.dss*.
Filename masks may be used to control *outputFile* naming convention. Example: ``%e:yyyyMMMdd_HHmm%.tin``.

-dssA <dssApart>
^^^^^^^^^^^^^^^^

DSS pathname A-part when saving to DSS

-dssB <dssBpart>
^^^^^^^^^^^^^^^^

DSS pathname B-part when saving to DSS

-dssC <dssCpart>
^^^^^^^^^^^^^^^^

DSS pathname C-part when saving to DSS

-dssF <dssFpart>
^^^^^^^^^^^^^^^^

DSS pathname F-part when saving to DSS

-type label
^^^^^^^^^^^

Datalabel. Default is 'Rainfall'

-inUnits <units>
^^^^^^^^^^^^^^^^

Input data units.
If unspecified, MetVue will attempt to determine *units* from input file.
If Metvue is unable to determine *units* from input file, Default is 'mm'.

-outUnits <units>
^^^^^^^^^^^^^^^^^
Output data units. Default is 'mm'.

-shg
^^^^
Output grids in Standard Hydrologic Grid (SHG) coordinate system.
Default output grid coordinate system is HRAP.
This option is only compatible with DSS image storage and will not work with MetVue native TIN output.

-title <title>
^^^^^^^^^^^^^^

Output file title. If unspecified, the program will attempt to generate a title from available information.
A title with spaces must be enclosed in double quotes. Example: ``\"My Title With Spaces\"``.

.. _gridreader-btime:

-bTime <time>
^^^^^^^^^^^^^

Beginning date and time. Used to constrain retrieval of TIN data to a specified timespan.
Accepts a :ref:`time-argument`.

.. _gridreader-etime:

-eTime <time>
^^^^^^^^^^^^^

Ending date and time. Used to constrain retrieval of TIN data to a specified timespan.
Accepts a :ref:`time-argument`.

.. _gridreader-dtime:

-dTime <timespan>
^^^^^^^^^^^^^^^^^

Duration of time from the beginning time or end time. Used to constrain retrieval of TIN data to a specified timespan.
Accepts a :ref:`timespan-argument`.

.. _gridreader-duration:

-duration <timespan>
^^^^^^^^^^^^^^^^^^^^

Constrain retrieval of TIN data to records having a duration of *timespan*.
Accepts a :ref:`timespan-argument`.

Example: '-duration 1Hour' will only use files or DSS records that have a 1-hour duration

.. _gridreader-shift:

-shift <timespan>
^^^^^^^^^^^^^^^^^

Temporally shift the image from its encoded time. Timespan can be negative (Example: -06:00:00).
Accepts a :ref:`timespan-argument`.

Can *not* be used with options **-bTime**, **-eTime**, **-dTime**, or **-localTime**.

.. _time-argument:

Time Argument
-------------

Time arguments represent a date and time and are used with options :ref:`gridreader-btime` and :ref:`gridreader-etime`.
Fixed notation and relative notation are supported.

.. admonition:: Time Argument: Fixed Notation

    **[yy]yy/mm/dd[,hh:mm:ss]**
    
    **ddmmmyy[yy],hhmmss]**
    
    **[yy]yyMMdd[hhmmss]**

    Definitions:

    [yy]yy
        Year (2018, 2019)
    mm
        Month (01, 02, 03 .. 12) or (Jan, Feb, Mar .. Dec)
    dd
        Day (01, 02, 03 .. 31)
    hh
        Hours (01 - 24)
    mm
        Minutes (00, 01, 02 .. 59)
    ss
        Seconds (00, 01, 02 .. 59)

.. admonition:: Time Argument: Relative Notation

    **T[{-|+}nnUU][@[[[[mm:]dd:]hh:]mm:]ss]**

    Definitions:
    
    T 
        Signifies current time. Optional - or + represent before or after current time.
    
    nn
        Amount to adjust T
    
    uu
        Units of time. Can be Y[ears], Mo[nths], D[ays], H[ours], M[inutes], S[econds].

    [@[[[[mm:]dd:]hh:]mm:]ss]
        A fixed portion for the date. If @ is specified, at least seconds 'ss' is required.

    .. admonition:: Examples
    
        -btime T-3D
            Starting time is 3 days prior to the current date/time

        -btime T+24H\@07:00:00
            Starting time is current time plus 24 hours, then adjust to 07:00:00 in the morning

        -btime T+1Month\@3:16:30:00
            Starting time is current time plus 1 month, then adjust to the third day of the month at 16:30:00.

.. _timespan-argument:

Timespan Argument
-----------------

Timespan arguments represent an amount of time and are used with options
:ref:`gridreader-dtime`, :ref:`gridreader-duration`, and :ref:`gridreader-shift`.

The amount of time is expressed in one of the following formats:

    **nnX** where nn is the number of intervals of the given interval type.
        
        Example: -dTime 10days or -dTime 3600seconds

    **ddd.hh:mm:ss** where days is optional but the hours minutes and seconds are required.
    
        Example: -dTime 4.8:11:00  (https://www.w3.org/TR/xmlschema11-2/#time specification)

    **PnYnMnDTnHnMnS** or **PnYnMnD** or **TnHnMnS**

        Example: -dTime P1Y2M3DT6H30M25S (https://www.w3.org/TR/xmlschema-2/#duration specification)

.. admonition:: Windows Users
    
    The character ``%`` must be escaped in any command line arguments.
    For example, the command ``-inFile C:/mydata/%yyyyMM%/%yyyyMMddHH%00z.rad...``
    is written as ``-inFile C:/mydata/%%yyyyMM%%/%%yyyyMMddHH%%00z.rad...``

.. note::

    Some providers require additional command line options.
    Additional provider options are documented HERE <- Add a link when this exists.
