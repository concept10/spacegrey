
Tribal knowledge requested to make organized sense of recommended E39 factory/dealer diagnostic hardware & software.

Based on the available diagnostic tools and in concert with the various BMW coding forums let's try to meaningfully organize the following E39-specific diagnostic-related scanning, coding, and programming tools & interfaces for the entire E39 tribe to benefit.
-----

    Assess your portable computer:
        Almost any laptop hardware will work
            The classic BMW dealer diagnostic laptop is an IBM T30
            You'll want at least 40GB available hard disk space (100GB+ if you're installing Progman)
            And, as much RAM as the PC can handle (Quick99Si had 2GB RAM in his Dell D620 laptop).
            However almost all Windows PCs should work though (best with WinXP).
                Warning: Most would NOT use their everyday laptop as their diagnostic laptop simply because software installation was intended for a stand-alone application (and, as such, it modifies many emulation, registry, and root entries).
        Most programs run on Windows (e.g., INPA & NCS).
            You can't go wrong with WinXP but others are reputed to work:
                Windows XP <== by far, the best
                Windows 2000
                Windows VISTA
                Windows 7 (NCSExpert requires XPmode)
            Some programs run on Windows only with UNIX emulation (e.g., EasyDIS & Progman).
                Typically EasyDis is set up on Windows via VMware UNIX emulation (details below)
                Typically Progman is set up on Windows via Daemon Tools UNIX emulation (details below)
        The biggest hardware factor on the PC is the I/O interface:
            USB (see details below)
            Serial (see details below)
    Order the right cable (1) (2) (3)
        Three constraints focus your cable decision:
            Vehicle end:
                20-pin round "pacman" OBD connector or 16-pin trapezoidal OBD connector
            Computer end:
                USB or RS232 serial
            Interface support:
                L-Line &/or K-Line &/or D-CAN
        20-pin round "pacman" OBD connector vs standard 16-pin "trapezoidal" OBD connector
            If your E39 has the round 20-pin "pacman" OBED connector in the engine bay, then you MUST use that connector with these tools.
                Note: It doesn't matter whether you 'also' have a 16-pin trapezoidal OBD connector; you still must use the round pacman OBD connector with your cables!
                Note: While the 20-pin round ADS pacman connector looks similar to the 20-pin round OBD pacman connector, no E39 uses the ADS interface!
            If you do not have the round 20-pin pacman OBD connector in your E39 engine bay, then you MUST use a 16-pin trapezoidal OBD interface cable.
        USB vs Serial
            USB is virtually 100% compatible with the software listed below and most recommend USB cables at this point.
            Serial cables are cheaper & more information exists about their use; but, as time goes on, USB is winning out over serial (as serial port laptops dwindle away).
            Most serial cables included adapters or cables to fit both the 20-pin round "pacman" OBD plug in addition to the 16-pin trapezoidal OBD port.
            Warning: Some serial-to-USB conversion cables work (1) (2); others don't. Try to avoid the hassle with good up-front decisions
        L-Line vs K-Line vs D-CAN
            L-Line is the communication protocol on BMW cars from circa 1987 (first year of the ADS connector) to about the 1997 (before the E39).
                Note that E39s (built from 1998 onward), do NOT use the ADS interface!
                Older E39s may have a similar 20-pin round pacman connector; but it's 'not' a round ADS interface; it's a round OBD interface.
                The round ADS interface uses pin 15 (RXD), which was phased out in 1996.
                None of the E39's should need an ADS interface, but if you have any doubt, check the voltage at pin 15 of your round pacman connector; if you see about 11v you need the round ADS interface. If not you need the round OBD interface.
                For further details, see the connector diagrams included below and the documents (e.g., bus system.pdf from JeffStri in post #94)
            K-Line is the communication protocol on BMW cars from around the end of L-LINE to around 2006, including all BMW E39s.
            D-CAN started on BMW in 2007 and is the current protocol (no E39 is D-CAN but most D-CAN cables are backward compatible to the K-Line).
        Warning: No cable (yet) handles all three interfaces!
            The best you can do is two out of three
                Serial cables are often L-Line & K-Line compatible
                USB cables are often K-Line & D-CAN compatible
                All E39s require at least the K-Line interface
            1st choice: BMW INPA EDIABAS K-Line USB Interface (e.g., USB K-Line, aka "BMW INPA EDIABAS K+CAN USB OBD2")
                $50 1, 2, 3
                Primary K-Line on pin 7 (for the engine & gearbox); secondary K-Line on pin 8 (for all else)
                FTDI Chip [Note: Get FTDI drivers here (1)]
                Works on all newer E39s from 2001 to 2003 with the 16-pin OBDII connector above the driver's left knee
                Note that there is a secondary K-Line on pin 8 (which is not on most DCAN interface cables) in addition to the primary K-Line on pin 7.
                Models that use the K-Line OBD interfaces are:
                - E87, E30 E36 E46 E83 and new E90, E34 E39 E53 and older E60 E61, E63 E64, E38 E65 E66, E31 E52, E53, E85 E52, R50 R52 R53
            2nd choice: BMW INPA EDIABAS K-Line Serial Interface (i.e., RS232 K-Line)
                $25, 1, 2, 3, ...
                Computer must have a serial port
                Usually comes as two cables, one for round 20-pin interface & one for the 16-pin OBD connector
            3rd choice: BMW INPA EDIABAS K+DCAN USB Interface (i.e., USB K-Line+DCAN)
                $120 1, 2, 3, 4, ...
                Be careful: There are TWO kinds of K+DCAN cables with respect to E39 compatibility
                    Primary K-Line on pin 7; secondary K-Line on pin 8
                    Pin 8 removed (needs adapter to restore 2nd K-Line)
                Models that require D-CAN:
                - E60, E61 after 3/2007, E83 after 9/2006, E81, E87 after 3/2007, E90, E91, E92, E93 after 3/2007,
                - E70 (New X5), R56 (New Mini), New F Series, as well as all other new models.
                Uses the FTDI FT232RL USB to Serial Converter chipset
            4th choice: BMW INPA EDIABAS ADS + K-Line USB Interface (e.g., RS232 ADS+K-Line)
                $65 1,
                This is the serial cable that Randomly & Quick99Si bought for their round pacman OBD interface cars, for $80, and which, unfortunately, needs a six-to-ten-foot serial port extension to be practical since it has a hard inflexible adapter.
                The connection is from round pacman connector to cable to adapter to computer or from OBD to adapter to computer; but realize since the adapter is a hard card, there's no way (without an additional flexible cable) that you can connect your computer physically!
                Works on older E39s from 1997 to 2000 with the 20-pin round pacman connector under the hood.
                If you have both the 16pin OBD2 socket AND the round 20pin socket you will still have to use the 20pin connector for factory diagnostics because not all modules talk to the OBD socket.
            5th choice: $35 Carsoft 6.5 RS232 Interface
                BMW INPA / EDIABAS RS232 (serial) Interface $20 (works on all E39s)
                Sabrent SBT-USC6M Hi-Speed USB 2.0 to Serial (9-pin) DB-9 RS-232 Adapter Cable
                Note that "tricks" are required to get the Carsoft 6.5 SP1 cable to work with INPA/EDIABAS & EasyDIS.
            6th choice: Volkswagon (modified) VAG-COM KKL 409.1 cables with a FT232RL chip.
                Note: ftdi chip USB drivers are here: http://www.ftdichip.com/Drivers/VCP.htm
                Apparently you need to modify the cables (1) (2) (3)
    Download the required Windows-helper software
        WinRar
            WinRAR 4.01 32-bit (1.4MB): http://www.win-rar.com/download.html
            Needed to extract the downloaded RAR files.
            This is a free 40-day trial version (which is plenty of time for what you need it for).
            Note: While most use WinRAR, any RAR archive unpacking tool will suffice, e.g., IZArc or FreeRarExtractFrog freeware, etc.
        Daemon Tools Lite (1)
            Daemon Tools Lite v4.41.3.0173 (10.9MB): http://www.disc-tools.com/download/daemon
            The purpose of this emulation software is to make the downloaded *.iso & *.nrg files on your hard disk 'look' (to the OS) like CDROM/DVD optical disc media (which is what the BMW diagnostic programs expect).
            Installation requires 29 MB of disk space.
            This is a free version with no time limit (for personal use only).
            For example, Daemon Tools will mount the INPA /EDIABAS *.nrg image file as a virtual cdrom (which includes inpa / ediabas / ncsexpert / winkfp / tool 32)
            Apparently, VMware has the ability to mount images also (based on Progman installation instructions); so Daemon Tools may not be needed if we can find instructions how to mount EasyDis v1.0 using VMWare instead of using Daemon Tools; however, the instruction PDF calls for Daemon tools so that's why it's listed here.
            Some instructions also note that Alcohol 120% trialware can be used for mounting ISO & NRG images as cdroms.
        VMware, v6 (315MB) (1) (2)
            VMWare v6.0.3-80004 (315MB): http://www.4shared.com/file/yAihspKS...-603-80004.htm
            The purpose of this software is to make the operating system (OS) of your PC 'look' (to the program) like UNIX, even though it's actually Windows.
            VMware is used for UNIX virtual-machine mounting when installing DIS/GT1 for the first time, and then again for VM-mounting the Progman hacked ISO.
            Note: Interestingly, the INPA v6.4.3 installation package (which includes INPA, the EDIABAS API, NCSExpert, WinKFP, & Tool32) requires another image file to be mounted as well (using daemon tools) because that virtual machine boots and uses the daemon-mounted image file to install the "EasyDIS/GT v44 programs"
    Download & install the required BMW-diagnostic software (only INPA/EDIABAS & EasyDIS are needed in most cases, both kindly re-imaged by Quick99Si for your convenience)
        1st INPA / EDIABAS package (i.e., INPA 4.4.7, EDIABAS 6.4.3, NCSExpert 3.0.8, NCSPlant 3.0.5, NFS 4.2, WINKFP 4.2.3, ToolSet32 3.2.4, & WINELDI 2.6.1)
            Download: http://quick99si3.home.comcast.net/bmw/INPA-6.4.3-full.rar
            How-To: http://quick99si3.home.comcast.net/b...LISH_SETUP.pdf (1MB)
                Notes: This version seems to be preferred over the optional 2010 v5.0.2 update.
                Set up version 6.4.3 to make sure everything works.
                Using WinRAR, point to the first RAR file & extract to create a folder called "INPA-6.4.3-full" containing the 347,183KB image "ediabas-6.4.3-full.nrg".
                Then mount that "ediabas-6.4.3-full.nrg" image file using the "Add Image" button in Daemon Tools Lite.
                It will mount, by default, as X:\NEU containing the folder X:\NEU\Referenz
                You will need to run the installation program X:\Referenz\INSTALL\Instprog.exe
                Follow the steps in the PDF file referenced above, but select the "BMW Group Rectification Programs USA" option instead of "UK" on page 5.
                On the same page, you can select the option to install NCS Expert and WINKFP in addition to INPA and EDIABAS (it's not required now, but it's useful for later).
            That INPA package contains INPA 4.4.7, the EDIABAS 6.4.3 API (which is required for most of the tools), NCSExpert 3.0.8, WinELDI 2.6.1, NCS plant 3.0.5, NFS 4.2, WinKFP 4.2, & ToolSet32 3.2.4 according to this reference.
            WINKFP can program, i.e., it can update software on a module to a newer release (if you already have that newer release file available)
            INPA is much easier to install than EasyDIS and will read module data, read & clear DTCs & perform car module function checks.
            INPA will read DTCs, clear DTCs and activate functions, e.g. turn on a warning light, or move the Xenon headlight aiming up & down in order to test functionality.
            While INPA is good for diagnostics, it will not do coding.
            INPA is easy to install. The install package simply copies files into the following four 8+3-named Windows directories C:\{EDIABAS,INPA,NCSEXPER,NFS}
            One then has to modify a couple of INI files to specify the adapter cable & you're in business.
            Note: Later versions of EDIABAS are known to cause problems with DIS and Progman so INPA v6.4.3 is the recommended version.
            ToolSet32 allows you to query detailed option information & is used for adjusting personal settings, key memory, & interrogating modules.
        NCS Expert
            NCS Expert is included in the INPA package listed above.
            NCS Expert is easy to install (if you already have INPA working, NCS Expert will work too, with no further changes).
            Can code dozens of options in every module in the car (e.g., the automatic door locking at 5mph in the General Module)
                See, for example this file:
                http://quick99si2.home.comcast.net/bmw/FSW_PSW.TXT
                That's the output Quick99Si obtained when he read his general module using NCSEXPERT.
                You'll see the following lines for allowing opening/closing of the windows via the remote.
                    KOMFORTOEFFNUNG_FB aktiv (i.e., comfort opening, FB=key fob)
                    KOMFORTSCHLIESSUNG_FB nicht_aktiv (i.e., comfort closing, FB=key fob)
            Most relate to different markets variants.
            Figuring out what to change to get a result can be very tricky.
            NCS Expert comes with virtually no documentation or detailed instructions.
            NCS Expert reads or writes to modules using parameters in German words and abbreviations.
            NCS Expert is difficult for a native German speaker to understand, let alone English speakers.
            If you want to "play around" & give your car a European flavor, NCS Expert is needed (e.g., Comfort Close, which EasyDis won't set).
            WARNING: Do not start NCSExpert until you've read the NCSExpert and dummy PDF's twice (NCSExpert is VERY dangerous and the GUI is in German to make it doubly more dangerous, in effect).
        2nd NCS for Dummies (also called NCS Made Easy or NCS Expert for Dummies, by Revtor)
            Note: For a description of the latest update from Revtor, please see this thread.
            For the latest download from Revtor, click here: http://revtor.be/ncsdummy/ncsdummy.zip
            For a Quick99Si archived download, Download: http://quick99si2.home.comcast.net/bmw/NCSDUMMY.rar (154KB)
                Note: NCSExpert needs profile files to read and write files. One of those profiles is included with Revtor's packages (it's the PFL file).
                Quick99Si kindly included two others sourced elsewhere.
                All these profile files are included in Quick99Si's NCSDUMMY along with the Revtor guiding PDF.
            Revtor has developed this very nice standalone (and much-needed) aid to understanding & using NCS Expert.
            For a five-minute walkthrough, using NCS for Dummies, please see post #50 below.
            The PFL file is a profile used later by NCSEXPERT.
            The included PDF is a guide on reprogramming, not installing, and it is definitely worth reviewing multiple times.
            This NCS for Dummies installation provides a detailed description of how NCS Expert works.
            It contains step by step guides for reading and writing to modules.
            It tells you how to make a backup of one's starting point, in case a coding change has unintended results.
            It reads NCS Expert input and output files with translations of many, although not all, of the hundreds of parameters from German to English.
            With these translations, one has a reasonable chance of success when trying to change (i.e. code) an option.
        3rd EasyDIS 1.0 (which is DIS v44) and the READTHISFIRST document from DavidMC
            Download 1: http://quick99si3.home.comcast.net/b...se-44-v1.0.rar (240MB)
            Download 2: http://quick99si2.home.comcast.net/b...4_programs.rar (758MB)
            How-to 1: http://quick99si3.home.comcast.net/b...THIS_FIRST.pdf (125KB)
                Note: Both files are needed; the first, EasyDIS-base-44-v1.0, installs via Daemon tools mounting; the second, GT1_v44_programs, is used later in the installation as described by "Gt1" in this guide http://forums.bimmerforums.com/forum....php?t=1297683
            How-to 2: http://quick99si3.home.comcast.net/b..._interface.mht (1.7MB) (bottom half for this step)
            How-to 3: http://forums.bimmerforums.com/forum....php?t=1297683 by Randomy (2.5MB)
            How-to 4: http://quick99si3.home.comcast.net/b...tion_Check.pdf (2.1MB)
            Notes: There are a few functions that will need to be performed from within the DIS virtual machine Administration menu.
                These include changing the translator to and from FISTER (ADS) or SOFTING (OBD) to correspond with your interface; performing the APITEST to verify functionality, configuring the running processis; and shutting down DIS.
                To do this, click the Administration button in the bottom right; select "Calibrating Touch Shield"; and enter 12345 as the password.
                VM should be set to "not run"; and the others should be set to "run."
                The "Installation_Check" PDF can be used to ensure that your entire configuration works.
                The toughest part is probably having the virtual machine properly networked to your Windows box with EDIABAS.
                Always run IFHSrv32.exe before starting DIS; in fact, it wouldn't hurt to have IFHSrv32.exe autostart with Windows.
            There is only one version of EasyDIS, which is EasyDIS 1.0 (more properly called "EasyDIS 1.0 based on DIS v44 and GT1").
            EasyDIS is a hacked version of DIS v44 that was modified to make installation and configuration in the UNIX virtual machine easier.
            DIS v44 was the dealer software for the E39 era & is the most useful software you can install.
            However, DIS runs on UNIX. Installation is difficult for most since one must set up to run DIS inside a UNIX virtual machine (via VMWare)
            EasyDIS diagnostics are excellent & the software is in English.
            EasyDIS does coding (e.g., the automatic door locking at 5mph in the General Module) and programming.
            EasyDIS exercises components & resets service intervals.
            All the Car & Key Programming options available in North America can be changed.
            New modules can be installed & retrofitted.
            Note: Do not install any later DIS than v44; DIS v45 to v57 are a step backward from DIS v44 because DIS became diagnostic only (Progman was added for coding/programming & confusingly has lower version numbers than DIS)
            Read the Randomly: How to install GT1\EasyDIS v44 step-by-step in the Bimmerforums Diagnostic Software forum ... The first post there is decently helpful as an overview, but, according to Quick99Si, it is outdated and lacking key details.
                For example, it doesn't say how to perform apitest in easydis; nor how to change the translator from softing (obd) to fister (ads); nor does it say that you need to exit DIS by shutting it down first (using the DIS administrator button, then calibrate the touch screen, then enter 12345 for a password, & then 0 to shutdown or other #'s to perform the apitest/translator/restart ediabas).
    Download any desired optional software
        4th Progman v32
            WARNING: Progman installation is more involved than those above!
                Don't even 'think' about installing Progman until you have the programs above in working order!
                Program requires a working EDIABAS API (which is installed with the INPA setup).
            Progman has a user friendly interface for coding & programming new modules than EasyDIS provides.
            But Progman has no more functionality than EasyDIS does (it is said Progman's primary benefit has to do with coding used modules)
                While brand new modules can be coded with EasyDIS/GT1, it seems that Progman is often used to code old (used) modules containing an old VIN that needs to be coded to the new VIN.
            Progman does not have any diagnostics; its sole purpose is programming and coding.
            Progman will, for example, code the automatic door lock feature at 5mph in the General Module.
            Progman runs under UNIX (so most people run it on Windows using VMware UNIX emulation).
            Confusingly, Progman version numbers started around v20 or so (superseding DIS v44).
            The currently available Progman version "in the wild" (i.e., outside BMW dealerships) is v32.
            There are those who say Program isn't worth the installation & learning trouble over EasyDIS.
            Note: Progman calls for the creation of another VMware virtual machine plus a whopping 80GB of virtual space. It needs another image mounted to CD so it can install itself, but the instructions here call to use VMWare for mounting instead of Daemon Tools.
        5th INPA 5.0.2 update
            INPA 5.0.2 update (480MB): http://quick99si3.home.comcast.net/b...02_Updated.rar
            Warning: It is unknown as yet whether this upgrade will work with the E39 (needs to be tested & reported back by someone).
            This probably isn't worth the risk & effort to install.
    Run your first coding experiment
        Spit out all the available options for your general module:
            Here's how, without even reading your car.
            Open NCS for Dummies.
                Select E39 for chassis
                Select GM3_C05 for module (or whatever your module is)
                "Translations" will be checked
                Manually check "Order Options"
                Click "Module Functions,"
                Click export sorted by keyword
                Save it somewhere and open the text file in Notepad
                You will have all the available options to code for that module (along with most English translations, and most importantly: the available "settings")
                For example, look for VERRIEGELUNGSSCHWELLE, and you'll see the speed settings you can change.
                This shows you'll likely want to set VERRIEGELN_AUT_AB_X_KM/H to nicht_aktiv and you're done!
        Change the automatic door locking feature of the E39 at a preset speed (e.g., at 5 mph, all four doors autolock):
            VERRIEGELN_AUT_AB_X_KM/H aktiv (i.e., automatically lock all doors at a specified speed)
                If it's aktiv, then VERRIEGELUNGSSCHWELLE is also used, which can accept a bunch of values representing various speeds
            VERRIEGELN_AUT_AB_X_KM/H nicht_aktiv (i.e., automatically lock all doors at a specified speed)
                If it's nicht_aktiv, then VERRIEGELUNGSSCHWELLE is ignored.
        Note: We need to flesh this out further for others to benefit.
    Run your first diagnostic experiment
        PLEASE IMPROVE!!! (help the team!)
            Test the ABS control module & wheel speed sensors

-----
ORGANIZATION: (please correct as needed!)

    Emulation Software:
        VMware used for UNIX virtual-machine mounting when installing DIS/GT1 for the first time, and then again for VM-mounting the Progman hacked ISO.
        Daemon Tools Lite used for virutal CDROM/DVD mounting of the ISO & NRG images downloaded of the BMW diagnostic software.
    Factory Software:
        INPA (the typical downloaded RAR file also installs the EDIABAS API, NCSExpert, WinKFP, & Tool32)
        NCS Expert (aka NCS)
        NFS
        ToolSet32
        WinKFP
    Factory Services:
        bmwtis.com,
    Dealer Software:
        DIS v44 (the dealer software of the E39 era)
        DISplus
        Progman
        ISIS (BMW software control system)
        ISTA/D (the current dealer level software)
        ISTA/P (the current dealer level software)
    Dealer Hardware:
        MoDiC
        GT1 1992-2004
        SSS
        ISIS
    Dealer Diagnostic Heads:
        OPS unit 2004-2009
        OPPS unit
        OPSis (OPS with DIS)
        ICOM (might be aftermarket)
    Aftermarket Software:
        Bavarian Technic Diagnostic Tool for BMW
        Carsoft Ultimate Home
        P.A. Soft BMW Scanner
        NCS made easy (aka NSC Expert for Dummys & NCS for Dummies)
    Aftermarket Hardware:
        IBM T30 laptop (serial port, running Windows, with VMware UNIX emulation)
    Hacked Software
        Carsoft 6.5 SP1
        EasyDIS v44 (this is the same as DIS except it was hacked to be easier to install)
    Hacker Hardware
        CAS3 mileage correction tool
    DIY Hardware:
        Actron
        AutoXray EZScan
        MaxiScan
        PEAKE
        SR-300
    Professional Hardware/Software:
        Autoboss V30
        Autologic
        Launch X431 Diagun
        Genisys EVO
        OMNITEC
        SnapOn Solus

-----
DEFINITIONS: (please correct as needed!)
Note: Each tool is roughly categorized as:
- Factory === Tools written by and for the BMW factory
- Dealer === Tools used by the dealer (supplied by the Factory)
- Professional === Tools used by professional mechanics (often > $1,000)
- Aftermarket === Tools intended for use by BMW aficionados (e.g., >$500 Carsoft Ultimate Home Edition)
- DIY === Tools intended for use by BMW dilettantes (e.g., <$100 OBD scanners)
- Hacker === Modified versions of the above (often out of China, often in German, often freely downloaded with no support, often with no cables supplied)
- HW === Hardware- SW === Software

    Actron = DIY HW, OBD scan/reset tool
    ADS = Active Diagnostic Plug, a round 20-pin pacman connection in BMWs from 1987 to 1997 (no E39 uses the ADS interface; the E39 20-pin round pacman connection is an OBD interface!)
    Autoboss V30 = Professional HW/SW, alternative to GT1, SSS, & ISIS
    Autologic = Professional HW/SW, alternative to GT1, SSS, and ISIS (aka Autologic diagnostics for BMW)
    AutoXray EZScan = DIY OBD scan/reset tool
    Bavarian Technic Diagnostic Tool for BMW = Aftermarket, Windows USB cable & diagnostic software package
    BMW Coding = setting/resetting available options in a module
    BMW Programming = either the set of instructions in a module (n), or updating the set of instructions (v)
    BMW Scanner = DIY diagnostic scan/reset tool using BMW factory codes (see P.A. Soft BMW Scanner)
    bmwtis.com = Factory service that allows coding & programming
    CAN BUS = Controller Area Network bus, ISO 15765, all US vehicles as of 2008 are required to meet CAN requirements (first in BMWs in the 1993 740i/iL)
    Carsoft 6.5 SP1 = Hacker beta PC diagnostic software service pack 1 (BMWs to 4/2004, requires RS232 serial port)
    Carsoft Ultimate Home = Aftermarket diagnostic PC software to read/reset fault codes & service intervals (aka poorman's GT1/DIS)
    CAS3 = a mileage correction tool that can read/edit/write eeproms for BMW CAS modules with Freescale MCUs,
    CIP = Dealer Coding, Individualization & Programming is a verb regarding allowing modules to be updated (aka Car & Key Programming)
    D-Bus = Diagnosis bus, introduced in BMWs in 1987 (the D-Bus is also known as TXD in BMW literature)
    DCAN = Protocol, a newer variant of the CAN protocol, used on BMWs built after 2007
    Diaghead = Factory diagnostic head, more powerful than an aftermarket interface cable (see also yellowhead)
    Diagun = Professional diagnostic tool, which communicates through bluetooth (see Launch X431)
    Digimaster II = Aftermarket key programming tool
    DIS = Dealer Diagnosis & Information System, UNIX software for the BMW dealer using the GT1 system, introduced in 1994
    DIS up to v44: Dealer software for the E39, performs coding, programming, diagnostics, read modules & DTCs, activate function tests, display live data, propose and step through tests to isolate faults for a DTC
    DIS after v44: Dealer diagnostic only (Progman became the dealer module used for coding & programing)
    DISplus = Dealer diagnostic & coding program update to DIS (see GT1)
    Do-it-auto = Cable interface, ADS, OBD, serial port, for use with INPA/EDIABAS software
    DLC = Data Link Connector (in practice, the trapezoidal OBD or round OBD connector itself)
    EasyDIS = Hacker, EasyDIS 1.0 is DIS v44 hacked for ease of Windows/UNIX installation, tedious to install, but user friendly (there is only one version of EasyDIS)
    EDIABAS = Factory coding & programming protocol named Electronic Diagnosis & Information Protocol
    EDIABAS = "Elektronik DIAgnose BASissystem, i.e., "Electronics diagnosis basic system"
    ELDI = Factory, aka WinELDI (installed with the INPA package)
    ELM327 bluetooth = Aftermarket scanner, can clear codes, view codes, look at PIDs (Coolant, Oil Temps, etc.)
    ELM3232 serial = Aftermarket scanner, can clear codes, view codes, look at PIDs (Coolant, Oil Temps, etc.)
    EPROM = Electrically Programmable Read Only Memory (remove old EPROM, insert new, & program)
    EEPROM = Electrically Erasable Programmable Read Only Memory (flashed without removing from module)
    Freelander = Land Rover Freelander, a vehicle that BMW INPA/EDIABAS diagnostic tools also work on
    FRU = Flat Rate Unit, every mechanic task is specified in FRUs, each FRU being "approximately" 5 minutes
    Genisys EVO = Professional diagnostic tool
    GT1 = Dealer Group Tester 1, a factory hardware & software testing & coding system used by BMW dealers up to 2005 (see DIS & DISplus)
    GT1 = Some people refer to the true dealer software, DIS v44 as GT1, even though GT1 is actually the hardware that came loaded with DIS software.
    I-Bus = Information bus, introduced in BMW E38 models, technically identical to the K-bus (body bus) except in use model
    ICOM = Integrated Communication Optical Module, works with ISIS, intended to replace BMW OPS & BMW OPPS diagnostic tools (aka BMW ICOM)
    INPA = Factory diagnostic interpreter program ? (no coding), user friendly (use INPA v6.4.3 for the BMW E39)
    INPA_2010 = 2010 version of BMW INPA (aka INPA v5.02)
    ISIS = Dealer Integrated Service Information Server (replaces DIS GT1/SSS/OPS and OPPS) software updating system
    ISTA = Dealer software currently in use (not available "in the wild")
    ISTA/D = Dealer software currently in use (not available in the wild)
    ISTA/P = Dealer software currently in use (not available in the wild)
    J1962 = the connector specification for the 16 pin OBD2 interface
    K-bus = body bus, technically identical to the I-bus, introduced in the BMW E38 model
    KKL = Cable interface, 1° K-Line on OBD-port pin 7 (for the engine & gearbox), 2° K-Line on pin 8 (for all else), & K data on the L line
    KSD = Kaufmännische Service Daten (Commercial Service Data that lists the FRUs (5 minutes each) per job)
    Launch's X431 = Professional diagnostic tool, which communicates through bluetooth (see also diagun)
    Launch Creader V = ?
    L-Line = Communication protocol on BMW cars from circa 1987 (first year of the round 20-pin ADS pacman connector) to 1997.
    M-bus = Motor bus, used exclusively between a climate-control module & a stepper motor to move vent air-distribution doors
    MaxiScan = DIY OBD scan/reset tool, cheapest CAN scanner that reads DTCs, pending codes, & clears codes
    MoDiC = Dealer "Mobile Diagnostic Computer" hardware/software bundle preceeding GT1
    MOST bus = Optical bus used on the E65 onward, primarily used for in-car entertainment electronics
    BYTEFLIGHT bus = Optical bus used on the E65 onward, serves predominantly safety-critical functions
    NCS = Factory, New Coding System edits parameters in modules using script files difficult to understand, (aka NCS Expert)
    NCS Expert = Factory, New Coding System edits parameters in modules using script files, di
    NCS = Factory, New Coding System edits parameters in modules using script files difficult to understand, (aka NCS Expert)
    NCS Expert = Factory, New Coding System edits parameters in modules using script files, difficult to understand (aka NCS)
    NCS Expert for Dummies = Aftermarket, by Revtor is a front end to NCS Expert (aka NCS Made Easy & NCS for Dummies)
    NCS Made Easy = Aftermarket, by Revtor is a front end to NCS Expert (aka NCS for Dummies & NCS Expert for Dummies)
    NCS for Dummies = Aftermarket, by Revtor is a front end to NCS Expert (aka NCS Made Easy & NCS Expert for Dummies)
    NCS Expert for Dummies = Aftermarket, by Revtor is a front end to NCS Expert (aka NCS Made Easy & NCS for Dummies)
    NFS = Factory New Flash System programming software used to flash control modules
    OMNITEC = This company appears to be the manufacturer of the factory/dealer interface & diagnostic heads.
    OPS unit = Dealer Optical Programming System, diagnostic head for 2006-2009 models that can't use GT1 (E65+)
    OPPS = Dealer, almost the same as OPS, except it does both diagnosis & programming with SSS & MOST (E65+)
    OPSis = Dealer HW/SW combination for E65+, an OPS unit with DIS software (aka Mini OPS)
    P-bus = Peripheral bus, used on ZKE-III vehicles, similar to the I/K-bus but is used only for body electronics
    P.A. Soft BMW Scanner = DIY diagnostic scan/reset tool using BMW factory codes (aka PASoft or PA Soft)
    PEAKE = DIY diagnostic scan/reset tool using BMW factory codes
    Progman = Dealer Program Management tool, tedious to install, but user friendly
    SR-300 = DIY OBD scan/reset tool
    SnapOn Solus = Professional diagnostic tool
    SSS = Dealer Software Service Station, UNIX HW/SW bundle superceeding GT1 for E65 onward (confusingly also the name of software that replaced DIS/Progman)
    SSS = UNIX program, superceded DIS & Progman (same functionality with improved UI)
    SSS = Some people use SSS and Program interchangeably even though they are actually different.
    Tacho universal Dash Programmer = ?
    ToolSet32 = Factory coding software (but not programming), a front end menu system for selecting between INPA, NCS Expert, & WinKFP (see Tool32)
    Tool32 = Factory, aka ToolSet32, the Windows 8+3 executable name used to perform various jobs, such as adjusting personal settings, key memory, interrogating modules, etc.
    VAG-COM KKL = Cable interface, Volkswagen diagnostic cable modified for BMW INPA/EDIABAS use (see also VCDS)
    VCDS = Cable interface, Volkswagen diagnostic cable modified for BMW INPA/EDIABAS use (see also VAG-COM KKL)
    VKM = Vehicle & Key Memory (1 of 6 coding & programming means (see ZCS, VO, EPROM, Flash, Coding Plug)
    VMWare = UNIX OS emulation on a Windows PC platform
    VO = Vehicle Order (one of six coding & programming means (see VKM, ZCS, EPROM, Flash, Coding Plug)
    WINELDI = Dealer, apparently this is Windows ELDI, which is BMW software inherent in the INPA package (unknown as yet what it does)
    WinKFP = Factory coding & programming software, updates modules, no documentation, can ruin your module
    Yellowhead = Hardware, the factory GT1 diagnostic head (i.e., interface cable) with test probes and wifi
    ZCS = Central Coding Key (one of six coding & programming means (see VKM, VO, EPROM, Flash, Coding Plug)
    ? what else ?

Let's ask each of us to please add and/or correct organization and/or definitions so that, at the end of this thread, we can finally summarize for the world, the relevant currently available 'things' & 'actions' for BMW diagnostic purposes.

ACTIONS:

    Coding tools: MoDiC, GT1/DIS, GT1/DISplus, SSS/Progman, Easy-DIS (to v44), NCS, NCS Expert, INPA, Carsoft (v7.x & v8.x only), Launch X431, ?
    Programming tools: MoDiC?, GT1/DIS?, SSS/Progman?, ?
    Diagnostic tools: Easy-DIS versions after v44, P.A. Soft BMW Scanner, ?
    Reset tools: Carsoft, Peake, ?
    Scanning tools: Actron, MaxiScan, SR300, AutoXray EZScan, ?

ORGANIZATION:

    Actions
        Coding (verb): setting available options that the programming in a module will recognize & permit (e.g., the door autolock feature)
        Programming (noun): the set of instructions stored in a module that give it functionality
        Programming (verb): loading updated BMW firmware into a module
        Reading: Reading error flags & diagnostic fault codes in a module & version and other information ?
        Resetting: ? Clearing error flags in a module ? (is it the same as coding?)
    Cables
        BMW INPA / Ediabas K+DCAN USB Interface (~$120)
        Chipsets:
            ADS interface (confusingly, no E39 uses the ADS interface! The round 20-pin pacman connector on the E39 is an OBD interface!)
            FTDI FT232Rx: VAGCOM KKL
            ?
    Protocols:CAN, D-CAN, K-CAN, PT-CAN, EDIABAS, ?
    Tools:
        Factory: INPA, ISIS?, NCS, NFS, WinKFP?
        Dealer: MoDiC, GT1/DIS, DISplus?, SSS/Progman, ISTA/D, ISTA/P
        Hacker: EasyDIS, INPA, NCS_expert?, NCS_made_easy, ?
        Professional: Autologic, Diagun, Genisys EVO, Launch's X431, SnapOn Solus, ?
        Aftermarket:
            BMW: Carsoft, Peake, P.A. Soft BMW Scanner, ?
            OBDII: Actron, MaxiScan, SR300, AutoXray EZ-Scan, ?

NOTE: Do not assume anything in this post is accurate (yet!) as I don't know anything; but I'm trying to organize this for all, including for me!

Summary of References:
- INPA, EDIABAS, NCS Expert, DIS, EasyDIS, Progman, & other BMW factory & dealer programming, coding, and diagnostic software (1) (2) (3) (4) (5) (6) (7) (8) (9) & related BMW diagnostic tools forums (1) (2) (3) (4) (5) & the most often recommended BMW diagnostic tools & cable interfaces (1)
