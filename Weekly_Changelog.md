project CMRemix/
commit 98ceb6ca421ae792f04254cfcc1d6633dfedf0bf
Author: Roman Birg <roman@cyngn.com>
Date:   Mon Apr 20 17:07:37 2015 -0700

    manifest: add Profiles trust agent
    
    Change-Id: I621c8074e3d35b1b2ec2953c3c03de7a53f29e8a
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit ce7745c0396a0fc8e5402e22389f510665cde136
Author: ZION959 <ziontran@gmail.com>
Date:   Fri Apr 24 20:27:10 2015 -0700

    track external_chromium_org

commit 097c5cdf3d78736d7cf90c1ad981c5acc63d1abb
Merge: ce7745c 98ceb6c
Author: ZION959 <ziontran@gmail.com>
Date:   Fri Apr 24 20:27:30 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

commit 7d4e6a5ad094fc0deb621a67f6b307a1bf0a6473
Author: ZION959 <ziontran@gmail.com>
Date:   Fri Apr 24 20:47:09 2015 -0700

    derp

commit ad1edc3d4524b3f0fc3466a44e6f2a3cb90815af
Author: ZION959 <ziontran@gmail.com>
Date:   Sun Apr 26 15:40:49 2015 -0700

    add dependencies for Qcom clangs v3.6

commit 91f917aa9e1911d8bccf87f6173d746d93a103eb
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 03:25:51 2015 -0700

    track development

commit 330b2937e85eb77e4eb3a66a13683c59dfbd58be
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 18:57:25 2015 -0700

    fixed prebuilts_ndk

commit ac181a21ce14b46fe11ce45e6594e10931d550d9
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 19:00:58 2015 -0700

    fixed copy and past again

project bionic/
commit b118cea1941a50a8b2bf445da8ec9a51016da605
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Mon Nov 24 22:12:22 2014 +0200

    Revert "Revert "Reenable support for non-PIE executables""
    
    * Conditionally revert under TARGET_NEEDS_NON_PIE_SUPPORT flag
    
    This reverts commit 76e289c026f11126fc88841b3019fd5bb419bb67.
    
    [mikeioannina]: Fix 5.1 compatibility
    
    Change-Id: I0c64f219c488f5a507b4e0d651b46f71d1c6b5be

commit 26ab57682d98786d877c1fb4425da2236a8ea6e5
Author: Colin Cross <ccross@android.com>
Date:   Wed Feb 11 17:40:45 2015 -0800

    Remove no-op sed step when compiling crtbrand.o
    
    crtbrand.c was compiled to a .s file, run through a sed script
    to translate a %progbits to %note, and the compiled to .o.
    However, when the sed command was copied from the original source
    it was not updated to use the new name of the section (.note.ABI-tag
    to .note.android.ident), so it didn't modify the file.  Since the
    section has been generated with type %progbits instead of %note for
    two years, just delete the whole sed step.
    
    Change-Id: Id78582e9b43b628afec4eed22a088283132f0742

commit e7d50c19c4062ec85882b7231c01232896cb029c
Author: Neil Fuller <nfuller@google.com>
Date:   Wed Apr 8 18:26:22 2015 +0100

    Upgrade timezone data to 2015b
    
      Changes affecting future time stamps
    
        Mongolia will start observing DST again this year, from the last
        Saturday in March at 02:00 to the last Saturday in September at 00:00.
        (Thanks to Ganbold Tsagaankhuu.)
    
        Palestine will start DST on March 28, not March 27.  Also,
        correct the fall 2014 transition from September 26 to October 24.
        Adjust future predictions accordingly.  (Thanks to Steffen Thorsen.)
    
      Changes affecting past time stamps
    
        The 1982 zone shift in Pacific/Easter has been corrected, fixing a 2015a
        regression.  (Thanks to Stuart Bishop for reporting the problem.)
    
        Some more zones have been turned into links, when they differed
        from existing zones only for older time stamps.  As usual,
        these changes affect UTC offsets in pre-1970 time stamps only.
        Their old contents have been moved to the 'backzone' file.
        The affected zones are: America/Antigua, America/Cayman,
        Pacific/Midway, and Pacific/Saipan.
    
      Changes affecting time zone abbreviations
    
        Correct the 1992-2010 DST abbreviation in Volgograd from "MSK" to "MSD".
        (Thanks to Hank W.)
    
    Bug: 19887183
    Change-Id: I1b4bdc5ae5cf778908a77893d7f8db8a4117e1e1

commit 93ee71a80772442aafe1176acad287077ab4f1b4
Author: Neil Fuller <nfuller@google.com>
Date:   Fri Apr 24 13:56:11 2015 +0100

    Update to tzdata 2015c
    
      Changes affecting future time stamps
    
        Egypt's spring-forward transition is at 24:00 on April's last Thursday,
        not 00:00 on April's last Friday.  2015's transition will therefore be on
        Thursday, April 30 at 24:00, not Friday, April 24 at 00:00.  Similar fixes
        apply to 2026, 2037, 2043, etc.  (Thanks to Steffen Thorsen.)
    
      Changes affecting past time stamps
    
        The following changes affect some pre-1991 Chile-related time stamps
        in America/Santiago, Antarctica/Palmer, and Pacific/Easter.
    
          The 1910 transition was January 10, not January 1.
    
          The 1918 transition was September 10, not September 1.
    
          The UTC-4 time observed from 1932 to 1942 is now considered to be
          standard time, not year-round DST.
    
          Santiago observed DST (UTC-3) from 1946-07-15 through 1946-08-31,
          then reverted to standard time, then switched its time zone to
          UTC-5 on 1947-04-01.
    
          Assume transitions before 1968 were at 00:00, since we have no data
          saying otherwise.
    
          The spring 1988 transition was 1988-10-09, not 1988-10-02.
          The fall 1990 transition was 1990-03-11, not 1990-03-18.
    
          Assume no UTC offset change for Pacific/Easter on 1890-01-01,
          and omit all transitions on Pacific/Easter from 1942 through 1946
          since we have no data suggesting that they existed.
    
        One more zone has been turned into a link, as it differed
        from an existing zone only for older time stamps.  As usual,
        this change affects UTC offsets in pre-1970 time stamps only.
        The zone's old contents have been moved to the 'backzone' file.
        The affected zone is America/Montreal.
    
    Bug: 20287125
    Change-Id: I8512c4e9ab09725395b256aba59ca34a23d1c995

commit 1bd09a9edb9b0aa3aaeb3eb8ab8f754822b6bc0f
Author: Neil Fuller <nfuller@google.com>
Date:   Tue Apr 28 17:03:13 2015 +0100

    Update to tzdata 2015d
    
      Changes affecting future time stamps
    
        Egypt will not observe DST in 2015 and will consider canceling it
        permanently.  For now, assume no DST indefinitely.
        (Thanks to Ahmed Nazmy and Tim Parenti.)
    
      Changes affecting past time stamps
    
        America/Whitehorse switched from UTC-9 to UTC-8 on 1967-05-28, not
        1966-07-01.  Also, Yukon's time zone history is documented better.
        (Thanks to Brian Inglis and Dennis Ferguson.)
    
      Change affecting past and future time zone abbreviations
    
        The abbreviations for Hawaii-Aleutian standard and daylight times
        have been changed from HAST/HADT to HST/HDT, as per US Government
        Printing Office style.  This affects only America/Adak since 1983,
        as America/Honolulu was already using the new style.
    
    Bug: 20551453
    Change-Id: I02364f15ca4ae20ed1a3b327f8517214bee938e5

commit 8d4fafee2a79418f43a8606f363eda06ca0abcfc
Author: Bernhard Rosenkränzer <Bernhard.Rosenkranzer@linaro.org>
Date:   Fri Apr 24 16:21:38 2015 +0200

    Define char16_t and char32_t to make gcc 5.1 happy
    
    gcc 5.1 doesn't define char16_t and char32_t (unless in C++ mode),
    causing compile failures.
    
    Change-Id: I08dcd13cdf8cd59a4a2f191864bedf4c0d1bb313
    Signed-off-by: Bernhard Rosenkränzer <Bernhard.Rosenkranzer@linaro.org>

commit 1f30a1e9b2455f164f34d920be1208cf04c7bb12
Merge: 4c16799 8d4fafe
Author: ZION959 <ziontran@gmail.com>
Date:   Thu Apr 30 10:48:45 2015 -0700

    Merge remote-tracking branch 'temasek/cm-12.1' into cm-12.1

project bootable/recovery/
commit 0225ffe3ff195eae032131b0c1ff9c9fb87fc047
Author: Danny Baumann <dannybaumann@web.de>
Date:   Mon Apr 20 11:27:18 2015 +0200

    Remove spammy debug output.
    
    Change-Id: Id152a6b57a8749fb6a68d8132bbd6bb5e87b7336

project build/
commit 5d282debcf980968a37ee287339b7f0c1373a168
Author: ZION959 <ziontran@gmail.com>
Date:   Fri Dec 12 23:06:47 2014 -0700

    cmRemiX Version
    
    Change-Id: I741e23c543db39afd5ebaa4ba3e8a65abd399be8

commit 2bf13db60d66dce633e2d34c29da82ed3cec733a
Author: Chet Kener <Cl3Kener@gmail.com>
Date:   Fri Dec 12 23:06:47 2014 -0700

    Introduce New Squisher/Opticharger for Lollipop (2/2)
    
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>
    Change-Id: I02b41274179cdc1793794fb11780ea60774e6e41

commit 239a9fb004283d8a9a325498673912be2847f976
Author: Jiangyi <sam.andrew.jiang@gmail.com>
Date:   Sun Dec 21 22:13:45 2014 -0700

    build: Add chromium prebuilt support to envsetup.sh && The core Makefile
    
    This adds a chromium_prebuilt function to envsetup.sh that is invoked by lunch to check
    whether the chromium prebuilt are up-to-date or not. If not, it will be built from source
    and then the new source built version will be pulled during brunch/mka bacon to become the
    new prebuilts for future builds.
    
    This is all opt-in through the USE_PREBUILT_CHROMIUM flag. Without it being set to 1,
    none of this would be ran, and regular operations will go on.
    
    PS13:
    -use export TARGET_DEVICE
    -replace git -C with params compatible to old git versions
    
    Change-Id: Ic372ef8183f20bb7ef8276dfa47c1dd6e63832f1

commit ba3ebbcbef2e23100ef03a7123c392b7748a885d
Author: Ayysir <ayysir@aospal.com>
Date:   Sun Dec 21 22:13:45 2014 -0700

    Prebuilt chromium: Run a check for target device directory
    
    This should fix the issue that arises if device fails
    and device is built again, chromium will error out because it thinks
    the prebuilt files exist (which they are not, directories are just created).
    
    Signed-off-by: Ayysir <ayysir@aospal.com>
    Change-Id: I595cab268e66c738ccae9900150b36d7f9626a6e

commit afa12ef75eb54337782f7c0cb7e8d5a1671c5976
Author: rooque <victor.rooque@gmail.com>
Date:   Sun Dec 21 22:13:45 2014 -0700

    build: Fix PreBuilt Chromium refs
    
    Change-Id: I57cc37d5200eb74110651fe40d93ce2192d0981e

commit 5d8f263bad74bcf1c12d591677c964faa80d85f9
Author: JoseGalRe <josegalre@gmail.com>
Date:   Sun Dec 21 22:13:45 2014 -0700

    build: change style console output of prebuilt chromium
    
    Change-Id: I2c390f3c64d614e181ebcad4e9711a93d9c55d44

commit 819063275b06b3358b07243b753314f120a87217
Author: JoseGalRe <josegalre@gmail.com>
Date:   Fri Mar 20 00:31:49 2015 -0700

    build: move chromium call...
    
    Change-Id: Ia91e750470f4af67487bf3e52d208bedc3a585dd
    
    Conflicts:
    	core/Makefile

commit 2dd810b4095e8148abb1d14604fb27dd61141548
Author: MaDc0w <MaDc0w@pac-rom.com>
Date:   Fri Mar 20 00:29:11 2015 -0700

    build: Rainbow unicorn puke [1/2]
    
    Change-Id: I393dd013194d73b293b361a42d42fa171ceee837
    
    Conflicts:
    	core/Makefile
    	envsetup.sh

commit 534aefe816e62605dc720ef3156cd7d472c85247
Author: Josue Rivera <prbassplayer@gmail.com>
Date:   Mon Feb 23 00:40:20 2015 -0700

    Add ro.cmremix.device for OTA porpuses
    
      * Due to unified builds disabling some id props, Slim OTA wasn't working
         working properly. Lets add a new prop just for our needs
    
    oldChange-Id: Ic2b3acb3dd4944160449f228cb69ec2c9f08775c
    Signed-off-by: Josue Rivera <prbassplayer@gmail.com>
    
    Conflicts:
    	tools/buildinfo.sh
    
    Change-Id: I745e0aa9e58040dc672815b2bf591ca17a65b21c

commit adcfa5dcf67486abcf2e95bf1bc9e4ae79f819e1
Author: kantjer <kantjer@gmail.com>
Date:   Mon Feb 23 00:43:04 2015 -0700

    Add ro.cmremix.model for OTA purposes
    
    Change-Id: I5d4baf0548e098d629e900580758a6d582d3cc2b
    
    Conflicts:
    	tools/buildinfo.sh

commit ca6cc1d4f0c2212627cd015656297e533c868cfe
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Dec 6 12:44:40 2014 +0100

    updater-script: Format system before installing ROM
    
    Change-Id: Ib266d6c1bde64a028a4d06bca40c5c1a1431edd0

commit b1e96aea3d84fbe47e8f25fd89d0f5bef4139b1f
Author: alviteri <davidteri91@gmail.com>
Date:   Sun Mar 22 23:06:37 2015 -0700

    Build: Changelog (3/3)
    
    Thanks David (crDroid Andrroid)
    Conflicts:
    	core/Makefile
    
    Conflicts:
    	core/Makefile
    
    Change-Id: I9b3086ab1178c02d97623416aeada51665df836c

commit 7fb1ee182a647a8745a171a590e6f9d2882b56d7
Author: MrBaNkS <banksmi09@gmail.com>
Date:   Wed Dec 31 19:44:19 2014 -0500

    build: remove all stops if using different make/openjdk-java version
    
    Change-Id: I9b48be859f0af9d3cd8e949eab7f6205edf11a70
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>

commit fe11fd0e90922025165831d9448af6d548170642
Author: Evan Anderson <evan1124@gmail.com>
Date:   Wed Dec 31 19:44:19 2014 -0500

    ccache: Use system version over prebuilt
    
    If there is a ccache binary on the
    host system use it instead of the
    AOSP prebuilt.
    
    Change-Id: I4b1e030713be22167a12bd229a4e35eda7736cd2
    Signed-off-by: Evan Anderson <evan1124@gmail.com>
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>
    
    (cherry picked from commit a74224f270183552ee2c2f0db16d24168f97a417)
    
    (cherry picked from commit a74224f270183552ee2c2f0db16d24168f97a417)

commit f4bef057f73a2c6c459d29e6d5af3272a8c2a200
Author: William Casey SEdlacek <w@sedlaceks.org>
Date:   Wed Dec 31 14:14:32 2014 -0500

    Block Building
    
    Change-Id: Id5c50c02f5bd737fc8b8ea785ebf536b82c09112

commit 6c60571d42f71ab3edf5f8c166fe7f52703f127e
Author: LorDClockaN <davor@losinj.com>
Date:   Wed Dec 31 14:14:32 2014 -0500

    Add SuperSU to releasetools
    
    Thanks to chinfire's "How to SU" guide,
    I've managed to get SuperSU zip flashing on every
    rom flash and it can easily be updated in
    vendor
    
    Also Settings part merged in from OmniRom
    
    PS2: Don't unmount /system, it gets unmounted
         from within superu.zip flash script
    
    Change-Id: I0f57f8c2b8733021c3c0b9a5fd3c343ae565a959
    Signed-off-by: LorDClockaN <davor@losinj.com>

commit 7335ee8bfd32009363bfd7b571f61c9968666716
Author: Chet Kener <Cl3Kener@gmail.com>
Date:   Wed Dec 31 14:14:32 2014 -0500

    Add a Whole bunch of Clean Options
    
    Change-Id: I5b32c79981fc32daba003e15865ee9df0721f092

commit d6c41c647922b19b2ddc5cb5edcab07582dd85ef
Author: Chet Kener <Cl3Kener@gmail.com>
Date:   Wed Dec 31 14:14:32 2014 -0500

    Add Make Dirty Option
    
    Change-Id: Ia51e8601822df5f3b8b9e94259cb4600d56f5d90
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>

commit 4b3b63c0c180cda5611036f94098c83badccc055
Author: SferaDev <sferadev@gmail.com>
Date:   Sun Nov 9 11:03:41 2014 +0000

    Don't stop if JDK version doesn't match
    
    Change-Id: I5e77c70724c7d81544673715ed09e0a53ce32730

commit d17a3516d1f814f9fbe04c6c23bbdc3b497fcf42
Author: mar-v-in <github@rvin.mooo.com>
Date:   Wed Dec 10 23:52:22 2014 +0100

    JDK8: JDK check should succeed with OpenJDK 8
    
    Change-Id: I1c1eaff7fa36bba2db261e0c5311bbc6d005a726

commit d87fa98ef3b14e5ad025b03386c345341b07c581
Author: Chet Kener <Cl3Kener@gmail.com>
Date:   Mon Nov 17 14:15:02 2014 -0500

    Add F2FS Compatibility
    
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>
    
    Add Missing Unmount
    
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>
    
    Remove Duplicate
    
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>
    
    Try 3 Options for Mount
    
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>
    
    Move Format Script to Bin
    
    * If backup script can be there so can this.  Besides there is no extras folder here anyways
    
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>
    
    Update this command for Lollipop
    
    * The previous command worked fine in Kitkat but this command is now what was needed to get the job done
    
    Change-Id: Iabebf6cf86cc66b4b546ddd34062ba633c2b74d1
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>

commit 7501388f24dc2d9858103c1af62567bcd1da797a
Author: fattire <f4ttire@gmail.com>
Date:   Mon Feb 16 01:19:08 2015 -0500

    repopick: Always expand paths to the repo executable.
    
    Change-Id: I4e89a530f98e3a28973c57adaf9046e9c21f1290

commit 199fad17c13cdf510d69e94490ff0ced49b386cd
Author: Chet Kener <Cl3Kener@gmail.com>
Date:   Tue Nov 4 21:33:02 2014 -0500

    Build Launcher3 instead of 2
    
    Change-Id: I36ca442f93ac0887021df7d6ca629dbc15440035
    Signed-off-by: Chet Kener <Cl3Kener@gmail.com>

commit ce42066e4d9cbccc2f63e38ae5d77b0c05a49ed0
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Feb 28 02:00:33 2015 -0700

    build: slim launcher
    
    Change-Id: I76149114e87e0bfffee52d2d73af4b6f1e477a8f

commit 879d0457fcaa82febfe472493fa89fb9f2bbb1c1
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Wed Feb 18 22:30:02 2015 -0700

    git: ignore gedit backups
    
    Change-Id: Iabb681842e1a9cc9ea450cafa97cf4d6135fb2b5

commit 87f48d29ba8a22b56f7afe8a1ef5b215cdee8a11
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sat Apr 18 23:20:21 2015 -0700

    Saberize v4 (2/2)
    
    Added -O3 modular optimizations.  To switch on use O3_OPTIMIZATIONS := true
    host gcc 4.8 is now default.  seems silly to have 4.6 as default.  To use host 4.6, set USE_LEGACY_GCC := true
    Add the updated version of graphite that works and set it on by default (top sabermod feature)
    cutomize arm neon to export flags to kernel
    
    Change-Id: I692f17c61029bc395910f4c976e4bc9bae7fdf50
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    arm: compile all thumb with -mthumb-interwork and cleanup -O3
    
    To enable this option use ENABLE_ARM_THUMB_INTERWORK := true
    
    This may slightly increase binary size but will include more arm
    instructions for increased performance.
    
    https://gcc.gnu.org/onlinedocs/gcc/ARM-Options.html
    
    Change-Id: I0ba0a2d34b84e34309c20ce0cbb85ea3ee6dda15
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Add Global posix thread aka pthread Support (1/2)
    
    this flag enables multithread support much like what I did in kitkat.
    
    https://github.com/SaberMod/android_build-OLD/commit/93d376380dffae1ec96eeb0ef00a7e663d107ca4
    
    Change-Id: Id5559ec460b2ba84ed9cfe7a47b0ac59544e1d61
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    pthread:  Make optional, disabled by default:
    
    This can cause high system RAM usage
    
    Change-Id: Ib038926b9c0b8ae150bc41f03afe20cb72b5d221
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Cleanup armv7-a-neon.mk for arm64 since AOSP has this hacked into armv7-a
    
    Change-Id: Icf85460fe2e508719ef996a35cb064a153f21305
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    libtinycompress: use kernel headers when used as a shared lib
    
    Change-Id: Ib6ceff06cf8f9b2780523b673f46b6dba6f46320
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    core combo linux-arm: filter TARGET_SM_AND to set gcc version
    
    Change-Id: If2619b5df2f305c31eeaae3780114c17758b5b33
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Allow NDK to be overrided with TARGET_NDK_VERSION
    
    Change-Id: Ic62b6ec76013bb93e82fba9578fbc61faf6d5cd0
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Revert "libtinycompress: use kernel headers when used as a shared lib"
    
    This reverts commit d944e7ad15801b7e79fed5b20f6ff4f433e8487a.
    
    Update binary.mk
    
    Change-Id: I7b398c3f08d4c33a882d2bdd086ca4f5c93af13f
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    GCC Freedom v3 for arm and arm64
    
    Change-Id: I3469aee460a95ab112f6fcd06738d46d92571822
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	core/combo/arch/arm/armv7-a-neon.mk

commit 9625e6db8bb4692731dea93bca47289cdff47296
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sat Apr 11 14:37:34 2015 -0600

    MOAR SaberMod flags (2/3)
    
    Change-Id: I213b582f5b2d3249c9e1d59135f54ad59c07326b
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit f6a6ff4cb30d78fdd40a66942d695bf481abfa81
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Tue Apr 14 13:48:34 2015 -0600

    ARM: Enable -fno-builtin-sin and -fno-strict-volatile-bitfields by default:
    
    No one uses anything less than gcc 4.6 anymore so stop using a
    redundant filter for it...
    
    Change-Id: Ib5cce3fe4d67f59a13542148de807487961cfcb3
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 820e5ee2cc506504da8516d645810e07b7f1387f
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Tue Apr 14 15:36:14 2015 -0600

    ARM: Fix typo: Fogot a "t"
    
    Change-Id: I69c6c578b55fdd84b2cb7c3759a5853dd7d0e46e
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit b3d748e860034babfba0f7e845fe3ab0aef5e55e
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Tue Apr 14 22:27:09 2015 -0600

    More message fixups...
    
    Change-Id: I9961268e46ba3514a078df07df1d61d0df3428f0
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 7400cd332d55c18d0d8e25b3b99d473b48bd063b
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Wed Apr 15 04:00:28 2015 -0600

    extra sabermod flags binary mode: separate gcc from clang completely
    
    Change-Id: I90c9d143632126282c9c7dc72c7867442be23546
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 990825c63171f12b1ab7155419dcc00cf9833365
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Thu Apr 16 00:44:38 2015 -0600

    Add some basic host optimizations (2/2)
    
    This is mostly beneficial when used with -O3 optimizations
    
    Change-Id: I53bab4e9edba04046a6e5f726749bba483ed92a9
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 74ab0591ee13ad716b98fff07fae9a23a91192c4
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Fri Apr 17 13:12:49 2015 -0600

    Cleanup graphite:  LOCAL_CFLAGS will be used for CPP flags
    
    Change-Id: Ida6dd67dbfb257b8c86bda3a1ead320d68847643
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 282ad11b05e3f1e33c6e91d8778c2c6eb58b22e5
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sun Apr 19 19:40:08 2015 -0700

    Build: Add Custom Toolchain Support
    
    Change-Id: I01d6024e344a07247a41be9759a8d9fe773b692e

commit 64a5e1b32d3851e1d8d84a7783bb6812d0950d0a
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Tue Apr 21 23:27:46 2015 -0600

    -O3 optimzations: More improvements (2/2)
    
    -Give a option to disable -O3 optimizations thumb.
     Some people feel this hinders performance and there was no
     solution found before to disable -O3 in binary mode previously.
     This patch allows this option, see description in binary.mk for more info.
    
    -Make extra loop flags dependent on LOCAL_O3_OPTIMIZATIONS_MODE := on
     We shouldn't really be performing extra loop optimizations unless -O3
     is enabled locally.
     And since these are not really considered -O3 flags according to gcc,
     they should remain in extra.mk (extra sabermod flags).
    
    Change-Id: Ie96aa4daddcea287f427ae3b3336b45e7faa152a
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    Cc: @frap129
    Cc: @ImTheReas0n
    Cc: @pbeeler
    Cc: Everyone else that wants notifications :)

commit b3a1ce0c9efd115d454f0079c5baa06e0baf40b8
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Wed Apr 22 02:44:56 2015 -0600

    Include sm_clear_vars.mk
    
    Change-Id: I21263efc50823f8f49f9cf3acfbf8553df5eb88a
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit cc146a5d29b9f03864407fd3f8d73bcfbf10c0b9
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Thu Apr 23 23:10:56 2015 -0700

    sm.mk: Bug fix for aosp and strict-aliasing (2/2)
    
    -For people have "other" strict-aliasing binary mode implimentations,
     then this is only needed when strict-aliasing is not set on.  In
     cases of "other" implimentations, this should be dependent on that
     being disabled.
    
    Change-Id: I613debaa3039ce6c601aa129911a314bc7c1eb80
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	core/binary.mk

commit 4607d00a31a54a9ae694f00096835e440969efb0
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Wed Apr 22 21:32:50 2015 -0600

    SaberMod ARM Mode (2/2)
    
    Only tested on user build for now.
    
    Change-Id: I1d92b2fe5ba4bbaa5bf662ffef32210a09521d92
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 389be1f8ecb512ac5f57f6ed1127ab031637d31e
Author: ZION959 <ziontran@gmail.com>
Date:   Fri Apr 24 17:50:02 2015 -0700

    Add SaberMod GCC & NDK GCC info to dumpvar
    
    Change-Id: Ifcb1f775079388058164a6cc0b1c7ed5ac129e91

commit 29db18ff3a7a1434a44a68b7c61b5b742aac733e
Author: ZION959 <ziontran@gmail.com>
Date:   Sun Apr 26 14:49:50 2015 -0700

    Compile TARGET MODULES with the Snapdragon LLVM Compiler 3.6 for Android instead of LLVM which comes with Android
    
    Credit all to MusterMaxMueller ( Many Thanks for all the help to have Qclang Optimization intergrated to CMRemix)
    
    https://developer.qualcomm.com/mobile-development/increase-app-performance/snapdragon-llvm-compiler-android
    
    Change-Id: I3889b8f0908be68dcf166223f960a057a46bf798

commit 7ffbd66ad1f8e887f571428d5bb9e64b24ea905c
Author: arter97 <qkrwngud825@gmail.com>
Date:   Tue Apr 7 18:44:50 2015 +0900

    Create 0 compression ratio jar files
    
    Modern devices now has a blazing fast NAND that storage speed is not the bottle-neck when it comes to reading apks.
    
    So use 0 compression ratio for improving speed and memory usage.
    
    Signed-off-by: arter97 <qkrwngud825@gmail.com>

commit 999ce745d904ec8d95c1ff5cd7c3de160cb00a84
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Mon Apr 27 15:30:58 2015 -0700

    small cleanup
    
    Change-Id: I337869199a70c5fad0ac6ce39a511b46b8dbee82
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	core/combo/TARGET_linux-arm.mk

commit f9c42b09d8bebdbc5f6eda63c1b185c76735e33e
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sun Apr 26 03:33:44 2015 -0600

    Rewrite SaberMod ARM Mode to fix build for arm64:
    
    ARM uses thumb by default and arm64 uses arm64 for default.
    
    Change-Id: Ie2addac9f8698928cba84690b812d48448900d0d
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit fe47bfcd6c79d15d2c34374933064eddba12f62a
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sun Apr 26 22:01:25 2015 -0600

    Find more strict-aliasing flags in arm mode
    
    Change-Id: Ibd039056c81548b3d43ade70c90b00d7e28cde3d
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit c5b57fdb441771ebf80f7ee41021fe62453f917a
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sun Apr 26 23:21:34 2015 -0600

    ARM: Make strict-aliasing optional
    
    Change-Id: I98f37ebec82b0a45ba575102937d3f1cd299cd74
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit bde393e7a58752ae07f857f493806cc0b676dd6f
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sun Apr 26 23:40:50 2015 -0600

    ARM: Remove -funswitch-loops from arm mode flags
    
    This is a -O3 optimization flag, so no need for it to be default.
    
    Change-Id: I7225144e236448a6b2e9f504f19c357f2f93e6db
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 9680311c3caad88d825c1c808f01cf5080bc5d5c
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Mon Apr 27 00:06:57 2015 -0600

    More flag fixes...
    
    Change-Id: Ibc621edd6ba5b1897831e0989b0df621a23a3b6e
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit d316535249c3f41977e27ecbf762e2f042cb6c87
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Mon Apr 27 00:35:45 2015 -0600

    sm.mk: code shrink
    
    Change-Id: Ie2b71913bba7bf8557a4fb9b4b22896eeb0c7ca3
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 43c7b7c531892369b0841db6f67e9ed46cc5308e
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Mon Apr 27 01:34:23 2015 -0600

    strict derp:  Make optional for real this time.
    
    Change-Id: I681d2a196b39571870b146883b3109e18f4168c0
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 10bee53ed72ac9230e36ae06c6ea282d8ee9b265
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Mon Apr 27 03:22:49 2015 -0600

    Remove extra clang -O3 flags
    
    Change-Id: Id691564dacde1f5f21877c0bbd341b5c7e5c8808
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 4eee37cc952a69f405b30d74bce8736240a13551
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Mon Apr 27 15:41:02 2015 -0700

    Create dumpvar.mk
    
    Change-Id: I33a262757d32eba377389abca58690edf668e566
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	core/dumpvar.mk

commit 757d1701e112ebb4c37d0fce29c13d932fcbbbb6
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Mon Apr 27 04:51:23 2015 -0600

    strict: one more fix..
    
    Change-Id: I108b5eaa196a8b8f6b27064466a189df66b9f354
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 7ce9014fe7a9224d7b5e2a75ad5b20af4a8397f1
Author: ZION959 <ziontran@gmail.com>
Date:   Mon Apr 27 21:53:15 2015 -0700

    derp

commit 97be58e71ec50d11eb4299d4b819a0a4350088f9
Author: ZION959 <ziontran@gmail.com>
Date:   Mon Apr 27 22:28:00 2015 -0700

    fixed build. Partial revert this commit
    
    https://github.com/CMRemix/android_build/commit/999ce745d904ec8d95c1ff5cd7c3de160cb00a84

commit cfc20667a3a9f572bd188563903891478d333c93
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Tue Apr 28 10:44:20 2015 -0600

    Add a option to disable vectorization flags (2/2)
    
    Change-Id: I2bd7a1a554b0680faa2da36be1866e8f57e0166c
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 3ae29bccd6304fba3b45d850d169bf649dd16ffc
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Wed Apr 29 13:11:59 2015 -0600

    Update for vendor changes
    
    Change-Id: I16418f4d80cc9ba4cdd557fe748d9d5d594401eb
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 50cbe76e881b78a82eb9e9fb8cceb1b12eeb995b
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Thu Apr 30 10:09:24 2015 -0600

    No optimizations for bluetooth modules
    
    Change-Id: If5b5b115be5e4affff55aa275055dcda61dffc3d
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

project device/samsung/hlte/
commit 6b115c7d776328ee882dc92cb3783db50b07ed6f
Author: ZION959 <ziontran@gmail.com>
Date:   Mon Apr 27 00:23:17 2015 -0700

    add varients kernel config
    
    Change-Id: Ibcd2e43a395d4b8943520420d588499ee0d8fee0

project device/samsung/hlte-common/
commit 99be1d260f8be0d26bb12c12b5d3201029887700
Author: ZION959 <ziontran@gmail.com>
Date:   Mon Apr 27 00:21:19 2015 -0700

    set zion mainline kernel config
    
    Change-Id: Id52a12b1b59c0063320bceafd5faf74680138292

project frameworks/av/
commit 0e03875bee979afe39bdbca30e23b15d7739171b
Author: Ricardo Cerqueira <ricardo@cyngn.com>
Date:   Sun Apr 26 00:57:04 2015 +0100

    audiopolicy: Apply FM volume control parameter for MTK hardware too
    
    MTK's audio uses the same parameter-based volume control for FM as QC,
    so share it
    
    Change-Id: I260cae9e85f2f668435746637a811c19ebc33857

commit ed8f87545ec85b137efc6d2cbe462429c7e0a66c
Merge: bdc78b5 0e03875
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 17:44:31 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

commit fb629ad8e893fb6f1817dbccb5178ab04de63f54
Author: RenJian <jian.ren@ck-telecom.com>
Date:   Wed Apr 15 11:32:15 2015 +0800

    Ensure there is no two same storages showing on the computer.
    
    [Preconditions]
    1. Insert a SIM card into phone and set the SIM lock as "on"
    2. Select MTP mode
    3. Power off the mobile
    
    [Procedures]
    1.Connected the phone and PC with usb cable
    2.Power on the phone->Input PIN code of SIM lock to enter the IDLE view
    3.Check the storage list on PC
    
    [Reproduce]
    Rarely
    
    Change-Id: I8efc3f812b669f2d4e2c3be89e3f97b5cc895628
    (cherry picked from commit 8b8d02886bd9fb8d5ad451c03e486cfad74aa74e)

commit bd4881c961173dd7b5aa4708a7444cc4d556c2ca
Author: Diogo Ferreira <defer@cyngn.com>
Date:   Wed Apr 29 17:36:32 2015 +0100

    stagefright: Configure codecs correctly in the mediatek platform
    
    We were setting the width/height as stride/sliceheight for both
    MTK and software codecs, which is wrong, it is only required in the
    former and will cause visual corruption in the later.
    
    Additionally, this adds buffer alignment which prevents MTK codecs
    from following a slower path.
    
    Finally, we're now also using stride/sliceheight whenever extracting
    a video frame.
    
    Change-Id: I3c40e17ad1757d3b27d919bf5378974b971aaacf

commit f519217633249883bcaaf6e79cc457cd2a50a2af
Author: Eric Laurent <elaurent@google.com>
Date:   Tue Oct 28 15:46:45 2014 -0700

    audio policy: validate stream type received from binder calls.
    
    Bug: 18001784.
    Bug: 18002005.
    
    Conflicts:
    	services/audiopolicy/AudioPolicyInterfaceImpl.cpp
    	services/audiopolicy/AudioPolicyInterfaceImplLegacy.cpp
    
    Change-Id: I8efa674dceff5a6e10251b1c7a55e9bb2d532395

commit 9fe3b80f53ed419e5dba1034e72f072e100beace
Author: Leena Winterrowd <lenhardw@codeaurora.org>
Date:   Wed Feb 25 14:28:52 2015 -0800

    mpeg2ts: Enable timestamp reordering for HEVC TS content
    
    If HEVC TS content contains B-frames and the frame rate is not
    explicitly set, the decoder may receive out-of-order timestamps
    which manifest as a/v sync issues. Enable timestamp reordering
    for HEVC content in the TS container to resolve such sync issues.
    
    CRs-Fixed: 801290
    Change-Id: I13a2fe382caebc07c8dc046a1344a1b73036cd2e

commit 4f684351042220af8e6fc9b501e12044d54a54b8
Author: Leena Winterrowd <lenhardw@codeaurora.org>
Date:   Thu Apr 2 11:41:59 2015 -0700

    mpeg2ts: Clean up HEVC format checks
    
    - Fix an invalid IDR frame check in ATSParser to avoid a crash on seek
    - Move custom HEVC TS parsing logic to private namespace
    
    CRs-Fixed: 808563
    Change-Id: I1c5ce6719fedd1e2cc9a68c04eb8a7ad795ad3c8

commit 4828d45d0c8d8f6bc144ee2e7d87a4e234246093
Author: Mingming Yin <mingming@codeaurora.org>
Date:   Tue Apr 14 14:14:20 2015 -0700

    Audioflinger: fix for hardware accelerated effects memory leak issue
    
    - Initialize hwAcc to NULL in AudioMixer constructor and delete allocated
      memory in deleteTrackName
    
    Change-Id: Iffe862d1d17345697ac7e233220c2e3f26343f77
    CRs-Fixed: 814304

commit fbe18e6c00c48145017d49c8e073e00348479abf
Author: Satya Krishna Pindiproli <satyak@codeaurora.org>
Date:   Mon Apr 20 12:04:01 2015 +0530

    audiopolicy: fix crash in camcorder during voice call
    
    - During an MO call when camcorder recording is done,
      a crash is observed for the first time.
    
    - The crash is due to an assert that fails because an
      inappropriate value is returned.
    
    - Fix the issue by returning NO_INIT to avoid the assert.
    
    CRs-Fixed: 823350
    Change-Id: Id83111957dab04a3db396401547989db8e8ed573

commit d851d899284fcb060be03a79196578ce48a11eb5
Author: Steve Kondik <steve@cyngn.com>
Date:   Tue Apr 28 23:20:32 2015 +0800

    Revert "nuplayer: Modify seek and resume latency calculation"
    
     * Dead code.
    
    This reverts commit 1aff8485242a72417615833d3522363c03ce9a31.
    
    Change-Id: I755f93368e3773add56178eb283b00f9bf8bbb69

commit ec8cc54df791d2000ae46f77e5052a00b4340a7f
Author: Steve Kondik <steve@cyngn.com>
Date:   Wed Apr 29 18:50:53 2015 +0800

    nuplayer: Fix bitrate propagation
    
     * We use "bitrate" rather than "bit-rate".
    
    Change-Id: I4699194e3e3f7ef55b4eb554f5de7a6b5f6b80ce

commit a024ef41bf8471bd2b8452bc01b2974ad2a5164c
Merge: ed8f875 ec8cc54
Author: ZION959 <ziontran@gmail.com>
Date:   Thu Apr 30 11:35:06 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1-2

project frameworks/base/
commit 370a23c727e5618f55184035784fbbd71e160e29
Author: d34d <clark@cyngn.com>
Date:   Mon Apr 13 12:08:49 2015 -0700

    Themes: Add palettized icon background support
    
    This feature allows a theme to supply a single icon background,
    usually a white or gray scale image, which will then be tinted using
    a color from a palette of six color styles.
    
    To use this new feature a theme designer will need to include the
    new <paletteback /> tag which has the following syntax:
    
    <paletteback
        img="name_of_png_drawable"
        swatchType=["vibrant" | "vibrantLight" | "vibrantDark" | "muted" | "mutedLight" | "mutedDark"]
        defaultSwatchColor1="hex_color"
        defaultSwatchColor2="hex_color"
        ⋮
        defaultSwatchColorN="hex_color"
        />
    
    ex:
    <paletteback
        img="iconback_palette"
        swatchType="vibrantDark"
        defaultSwatchColor1="#009688"
        defaultSwatchColor2="#cc0000"
        defaultSwatchColor3="#ff8800"
        />
    
    You should specify some default swatch colors for those cases when
    the original icon did not have any colors to match the swatchType
    you requested. If no default swatch colors are defined, the original
    un-tinted background will be used.
    
    Change-Id: Ifd6dd65cc34ad4cd966fa9670f68704ac5671960

commit 73ca08bd8359d038276b03d1df0276cad86d21a0
Author: tobitege <tobiasteschner@googlemail.com>
Date:   Thu Apr 23 14:02:35 2015 +0200

    Fix NPE in NetdResponseCode.InterfaceClassActivity
    
    Under circumstances the 4th param is null and causes NPE.
    Exception looks like this in logcat:
    E/NetdConnector( 1086): Error handling '613 IfaceClass idle (null)':
    java.lang.NumberFormatException: Invalid int: "(null)"
    
    Change-Id: Id1bbbeeec8452e7103c4213be7b3029c6d36fa55

commit 13b82980a8e15ff6f4f48448931b4ad4e5a5251d
Author: Altaf-Mahdi <altaf.mahdi@gmail.com>
Date:   Tue Apr 21 14:48:44 2015 +0100

    Base: fix facelock crash when lock screen is disabled
    
    Change-Id: I44e2cef77f0e9119a0584aea548151687b9e35fa

commit 9f23efd57e18e04706b57aa261ec16d6d0739e01
Author: Roman Birg <roman@cyngn.com>
Date:   Mon Apr 20 16:22:12 2015 -0700

    frameworks: prepare for Profiles trust agent
    
    Remove checks for Profile.LockMode.INSECURE.
    This logic will be handled by the Trust Agent API now.
    
    Change-Id: I035911d7d8f3f9c8006eb4256fb8332f172bab1b
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 01b540954bd99b478429a7f0db7868a0c5512af7
Author: Roman Birg <roman@cyngn.com>
Date:   Wed Apr 22 10:33:19 2015 -0700

    SystemUI: improve visualier tile state management
    
    Always listen for audio session changes while tile exists so state is
    never stale. Only refresh UI while listening. Only attach visualizer
    while listening.
    
    Change-Id: Iadd99c42074f5390b397c0d979731ace80a23b76
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 62575a4e3574ebfb22258ce622805114c55b7526
Author: Ondrej Zima <keltuv.email@gmail.com>
Date:   Tue Apr 21 19:34:01 2015 +0200

    Framework: CS translation
    
    - fixed really bad construction
    
    Change-Id: Ide743ffdf8f652d944a729aea62d78b91fc8a13b

commit fb332a51b1d1405e21a652e52ab6283ca79d2094
Author: Dan Pasanen <dan.pasanen@gmail.com>
Date:   Wed Mar 18 23:46:15 2015 -0500

    ConnectivityService: add persist.radio.noril
    
    * For those of us with a tablet or device that has a radio, but
      don't plan to ever use it
    
    Change-Id: I8b1a5805254b549886eb5b08005fb92e97a6b7ce

commit 4de6db65e4bc1ef028754bac04a86cc073df42d7
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:13:26 2015 +0300

    Automatic translation import
    
    Change-Id: I3731f2e6891fc443a7f87d80e00371567f288a7d

commit 46a4e9fb694daf2560aa9bfc117d4ab230aff1cd
Author: Adnan Begovic <adnan@cyngn.com>
Date:   Tue Apr 21 16:11:51 2015 -0700

    Telecomm: Fix doc-comment-check for linking of hidden API.
    
      frameworks/base/telecomm/java/android/telecom/TelecomManager.java:36:
          error 108: Link to hidden class: PhoneAccount label=PhoneAccount
      DroidDoc took 447 sec. to write docs to /Volumes/android/out/target/common/docs/doc-comment-check
    Change-Id: Id709bc7c2eca8f309e210191887c3a272f3815ad

commit d8cf50f5bf306e5e5bab72d649e039c3c00b976d
Author: Adnan Begovic <adnan@cyngn.com>
Date:   Mon Apr 20 15:38:56 2015 -0700

    NotificationMgr: Only do DOS protection if not updating a notification.
    
      Only check for DOS protection if the incoming id being sent by the callee is
      unknown to us. Otherwise, you can post MAX_PACKAGE_NOTIFICATIONS and never
      be able to update any of them without first cancelling an existing notification.
    
    Change-Id: Ideab9a3d01a45e15942db63864f964b3a3308611

commit 02144d8ca67ff14c840a0af4263cfdddfe0fad43
Author: Roman Birg <roman@cyngn.com>
Date:   Tue Apr 21 13:13:06 2015 -0700

    SystemUI: add a disabled state for Quick Tiles
    
    Some tiles may want to be visible, but not allow any user interaction
    due to security reasons. Add a visual disabled state for tiles which are
    not enabled.
    
    With this patch, the Profiles tile and the Lockscreen toggle tile
    disable themselves on a secure lock screen.
    
    Change-Id: I65ec7837661483d238d8dc3fa18419f76c8029dd
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit d892e183fba0ec4b3837968d8c0a3a6ffbe77ee6
Author: wangjing <wangjing@codeaurora.org>
Date:   Thu Apr 9 16:16:17 2015 +0800

    SystemUI: Set Occluded to false when keyguard is not showing
    
    When quiting incall view, "Occluded" was not set to false, then
    it fitted system window in keyguard view, so status bar display a
    new black bar.
    
    Set Occluded to false when keyguard is not showing.
    
    Change-Id: Icb87def557e783c61a13f0de752b37324de8c6c0
    CRs-Fixed: 809699

commit a55f9db19f0d21b10ed56bb8ffa77611d82ee8aa
Author: Uday Kiran Jandhyala <ukiran@codeaurora.org>
Date:   Wed Apr 8 19:05:14 2015 +0800

    Black Screen: Fix dlfree error when delet mZipInflater.
    
    _CompressedAsset::close() and _CompressedAsset::getBuffer() may
    delete mZipInflater object without mutex protection. This may cause
    race condition during two thread try to delete mZipInflater object
    at the same time. Fix this issue by adding auto local mutex lock in
    _CompressedAsset::close() and _CompressedAsset::getBuffer().
    
    CRs-Fixed: 822097
    
    Change-Id: I7c8d2e308e196db54c6a91bc2d16545b331f87bc

commit 9617feb6184ad8d2db04e4e8a62ee342860cbd86
Author: Lars Greiss <kufikugel@googlemail.com>
Date:   Sat Apr 25 03:01:35 2015 +0300

    Launch app privacy settings when tapping on PG notification (1/2)
    
    Based on https://github.com/SlimRoms/frameworks_base/commit/97ccae06cd0ad1aa366c3a70e8e744277c409b06
    
    JIRA: CYAN-6077
    Change-Id: I8632e8c944c1d5d7ad2fb2a2276bae5fe2d4a0a0

commit fc5ede4fd670bffcaca263249627b0584c53a275
Author: DvTonder <david.vantonder@gmail.com>
Date:   Sat Apr 25 01:06:17 2015 -0700

    Frameworks: Allow/Prevent notification light in Zen mode (1 of 2)
    
    This allows the user to prevent the notification lights from showing during Zen mode as per Android 5.0.x
    
    Change-Id: I831c475204c8647d8ee281094aca837ee9594eb4
    
    Conflicts:
    	core/java/android/provider/Settings.java

commit 4259fd26e636a3930d9fc8012237cc93c4e27788
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 01:20:58 2015 -0700

    Revert "Option to use volume keys to control media volume anytime [1/2]"
    
    This reverts commit ce574fb80b28e8de76462ec059ed4c6a332d39a1.
    
    Conflicts:
    
    	core/java/android/provider/Settings.java
    
    Change-Id: I4dcc23c8bca98a2311173083c34fd95914c1d7de

commit 38e5b5bd94d67d2e8342a03fb220b702adacd5a4
Author: Pawit Pornkitprasan <p.pawit@gmail.com>
Date:   Sat Apr 25 01:25:09 2015 -0700

    Option to use volume keys to control media volume anytime (2/2)
    
    See Settings part for description
    
    Change-Id: I78d26b0bd41f5b58514ae9c68208a8c950396823
    
    Conflicts:
    
    	media/java/android/media/AudioService.java
    
    Conflicts:
    	core/java/android/provider/Settings.java

commit 19554c8aa6c53deab3c68768be490c71eb7022e7
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 16:12:09 2015 -0700

    [Squash] Revert Slim Stuffs
    
    Revert: Framework: SlimAction as QuickTile (1/2)
    
    Configure which Slim actions you want to use as tile and then add the 'SlimAction' tile.
    Single press will switch between Slim actions and long press will execute the Slim action. If the tile has only one Slim action, single press will execute the action.
    
    Screw'd:
    Modified for Screw'd AOSP sources
    
    Change-Id: I229b2163152f73b4870878837117204dd0aad960
    
    Conflicts:
    	core/java/android/provider/Settings.java
    	core/java/com/android/internal/util/cm/QSConstants.java
    	packages/SystemUI/src/com/android/systemui/statusbar/phone/QSTileHost.java
    
    Conflicts:
    	core/java/android/provider/Settings.java
    
    Conflicts:
    	core/java/android/provider/Settings.java
    	core/java/com/android/internal/util/cm/QSConstants.java
    	packages/SystemUI/src/com/android/systemui/statusbar/phone/QSTileHost.java (reverted from commit 7e4d255cf5f6e4aaa980013bf2d5d0f36592ef90)
    Revert: Action: Add kill-app and last-app actions
    
    Forward port from KitKat
    
    Change-Id: If8326ffed21faa2452e22b2afb717f4c123bd2a0
    
    Conflicts:
    	core/java/com/android/internal/statusbar/IStatusBar.aidl
    	core/java/com/android/internal/statusbar/IStatusBarService.aidl
    	packages/SystemUI/src/com/android/systemui/statusbar/CommandQueue.java
    
    Conflicts:
    	packages/SystemUI/res/values/cr_strings.xml
    	packages/SystemUI/src/com/android/systemui/statusbar/BaseStatusBar.java
    
    Conflicts:
    	packages/SystemUI/src/com/android/systemui/statusbar/CommandQueue.java (reverted from commit de238bc085a357f458fece6597ebc2ac96313a97)
    Revert: Action: Add screenshot action
    
    Change-Id: I98960f6bc9987da763342f491611dc54c44fca43
    
    Conflicts:
    	packages/SystemUI/src/com/android/systemui/statusbar/CommandQueue.java
    
    Conflicts:
    	packages/SystemUI/src/com/android/systemui/statusbar/CommandQueue.java (reverted from commit 085be268d7e5b19feb49f30f6ddb3bf3406f6077)
    Revert "[1/2] Base: Configurable overflow menu button"
    
    This reverts commit 4df3814aa871cb4a1eeaa4a94151025d00599a4a.
    
    Change-Id: If96ae5df993232f0aba51b46e5fa25fef86a7850

commit efe045f6f3603e5edd52f46338c6fbc3315b7dbf
Author: Dragon <dragon7780@hotmail.nl>
Date:   Sat Apr 25 16:17:37 2015 -0700

    Base: SlimPie (1/2)
    Implement SlimPie for lp5.0 ported from kitkat.
    
    PS1: Implement SlimPie for KDP
    
    PS2: Fx some derp!
    
    WIP
    Still need to bring back a few more slimpie features.
    
    Signed-off-by: Dragon <dragon7780@hotmail.nl>
    
    Change-Id: Ib74c5fa40c90825177d088bf6f76cd8636b79cc2
    
    Conflicts:
    	core/java/android/provider/Settings.java
    	packages/SystemUI/res/values/cr_colors.xml
    	packages/SystemUI/res/values/cr_dimens.xml
    	packages/SystemUI/res/values/cr_strings.xml
    	packages/SystemUI/src/com/android/systemui/statusbar/CommandQueue.java

commit a8275f210bc242b97a20f4d16dc8901d2cf881b2
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Apr 25 16:17:37 2015 -0700

    Action: Add kill-app and last-app actions
    
    Forward port from KitKat
    
    Change-Id: If8326ffed21faa2452e22b2afb717f4c123bd2a0
    
    Conflicts:
    	core/java/com/android/internal/statusbar/IStatusBar.aidl
    	core/java/com/android/internal/statusbar/IStatusBarService.aidl
    	packages/SystemUI/res/values/cr_strings.xml
    	packages/SystemUI/src/com/android/systemui/statusbar/BaseStatusBar.java
    	packages/SystemUI/src/com/android/systemui/statusbar/CommandQueue.java
    
    Conflicts:
    	packages/SystemUI/res/values/cmr_strings.xml

commit 60419f0dcd7ae94863a580d8df8e9c859fe71268
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Apr 25 16:17:37 2015 -0700

    Action: Add screenshot action
    
    Change-Id: I98960f6bc9987da763342f491611dc54c44fca43
    
    Conflicts:
    	packages/SystemUI/src/com/android/systemui/statusbar/CommandQueue.java

commit 58015573317b62fd4b23ed7da7629546de50bec2
Author: Trishool Narayanasetty <tnarayan@codeaurora.org>
Date:   Sat Apr 25 16:17:37 2015 -0700

    frameworks/base: Make minfree values optimal for 32bit devices
    
    This change makes lowmemorykiller minfree values optimal for 32bit
    devices. Arrived at these values after evaluating UX and launch
    latencies.
    
    Change-Id: Ia797ead2d330ec3347ee964ac5ec3dd6513134a4
    
    Patchset: 1
    http://review.cyanogenmod.org/#/c/96187/

commit ec575a1de0f27bbff360ee6ced08575b710ac0d0
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 19:10:00 2015 -0700

    Revert: App sidebar: notify if app is not installed
    
    better than force close
    
    Change-Id: I9eebe1a3a4be2dad16ed9a8cff9c0694900d833d (reverted from commit 988d73b0b2e47c5c9bce8428cffd3d9004b97f3a)

commit 5e5cef254474a64db7dcf3f2d480942fb614770a
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 19:12:42 2015 -0700

    Revert: App sidebar: some adjustments
    - Cleanup
    - fix disappearing appbar on changing appbar position
    - may fix endless FC on changing appbar contents
    
    Change-Id: I2e94290dc128447f0da8937eb5dc0ed10296a155
    
    Conflicts:
    	packages/SystemUI/src/com/android/systemui/statusbar/phone/PhoneStatusBar.java
    
    Conflicts:
    	packages/SystemUI/src/com/android/systemui/statusbar/phone/PhoneStatusBar.java (reverted from commit 8a71a12daa5d4d5e19dbfe4257b4083053ec3ca3)

commit 8b5e45477ce9520b95cdc7c00c8315f2f6b1b19e
Author: d34d <clark@cyngn.com>
Date:   Thu Apr 23 20:25:35 2015 -0700

    Themes: Add rotation and translation to composed icons
    
    This feature allows a theme to specify a rotation and translation
    in addition to scaling the original icon when composing.
    
    To use this new feature a theme designer will need to include the
    <rotate /> and/or <translate /> tags with the following syntax:
    
    <rotate angle="angle_to_rotate" />
        where angle_to_rotate can be from 0 to 360 degrees
    
    <translate xOffset="x_value" yOffset="y_value" />
        where x_value and y_value are device indipendent pixels
        and can be any value (both positive and negative depending
        on which way you want to move the icon)
    
    ex:
    <rotate angle="45"/>
    <translate xOffset="-10" yTranslate="15"/>
    
    Change-Id: I37ccf7861d22ee3aa21fce25e7e1b1afc49b3bcc

commit 9cffb83cf0278e57c13f6bb25f6ca6081a42b5f7
Author: dhacker29 <dhackerdvm@gmail.com>
Date:   Sat Apr 25 02:02:50 2015 -0400

    SettingsProvider: Make the default battery style Circle
    
    This will allow us to remove the overlay in vendor/cm so devices
    with no battery, aka fugu, can override this to none.
    
    Change-Id: Idb8decc5e999849e3fe3d6b72419dd3d96ff1ad2

commit 39385846351efa6b46ed1bd7d168d5ceceb47155
Author: cristianomatos <cristianobmatos@gmail.com>
Date:   Sun Apr 26 11:54:15 2015 -0700

    Add lastapp/killapp/screenshots to actions
    
    Reference
    https://github.com/temasek/android_frameworks_base/commit/900d251187944faea5ea4f1ab2f97481fa810d80
    
    Authorship to cristianomatos
    
    Forward ported to cm-12.1 to temasek build
    
    Conflicts:
    	packages/SystemUI/res/drawable-hdpi/ic_sysbar_lastapp.png
    	packages/SystemUI/res/drawable-mdpi/ic_sysbar_lastapp.png
    	packages/SystemUI/res/drawable-xhdpi/ic_sysbar_lastapp.png
    	packages/SystemUI/res/drawable-xxhdpi/ic_sysbar_lastapp.png

commit 4ceff02678cddae8f6d45f9043dcb9a5f63e5f38
Author: Janson Kang <temasek71@gmail.com>
Date:   Sun Apr 26 17:28:05 2015 +0800

    SystemUI: Reset status bar clock color before hiding
    
    This fixes status bar clock re-appearing after hiding

commit 63dd05bb50265a265e2eaac92e383d4c3469acdd
Author: Janson Kang <temasek71@gmail.com>
Date:   Sun Apr 26 20:20:52 2015 +0800

    Fix heads up tile

commit ee42ce56fe05bc0156f279324e07472bc0fa97f0
Author: padarshr <padarshr@codeaurora.org>
Date:   Fri Jan 23 18:51:36 2015 +0530

    Bootanimation crashes if Audio is not ready
    
    This change makes sure bootanimation does
    not crash even if Audio is not up.
    
    Change-Id: I3ef510bf7fc26008eacbe02957a34cdccda2b548

commit 9ddfc354dafd9b830dfd30f0ff5c2baf5df9de6e
Author: Chaitanya Saggurthi <csaggurt@codeaurora.org>
Date:   Wed Apr 15 20:48:48 2015 +0530

    Fix system server crash
    
    Fix system server crash by adding null check to
    subscriptionManger API for isub service.
    
    Change-Id: Ie113ae110136979b00bd5f254baff02182b2ce53
    CRs-Fixed: 822865

commit 77f339a4c59b4031ae9517e4baf838c3df7ccee2
Author: Muhammed Siju <msiju@codeaurora.org>
Date:   Thu Mar 19 21:27:12 2015 +0530

    IMSVT: Fix data usage value.
    
    Data usage value was always received as 0 due to
    wrong API used for sending Message.
    
    Change-Id: I4626e51f28f64a33fcb6245da9cdbdca36a8215d
    CRs-Fixed: 810409

commit caffb622f02e52875ee262c9931a6ea08b3c4160
Author: Omkar Kolangade <omkark@codeaurora.org>
Date:   Mon Mar 23 17:51:16 2015 -0700

    IMS Connection Capabilities Update
    
    IMS connection capabilities were not getting
    propagated to the upper layers whenever a
    capability was added or removed. Adding the
    same.
    
    Change-Id: Ic67d76df05c8b2a1b8abaf27f266fe9693764e52
    CRs-Fixed: 806868

commit 0d6bb968c7969efc6cf67f1ef0cc340d57e6ea93
Author: Suchand Ghosh <suchan@codeaurora.org>
Date:   Fri Feb 27 13:47:53 2015 +0530

    IMS: Allow add participant with normal IMS call.
    
    We should allow add participant with normal IMS
    call to make it conference.
    Send add participant through existing connection
    of normal IMS call.
    
    Change-Id: Ia634b10addc682bd9a41ae2273228345f1181953
    CRs-Fixed: 800563

commit ae7e2679cd38415a39e0462f4eabc7b0aab42159
Author: Ravinder Konka <rkonka@codeaurora.org>
Date:   Wed Jan 21 20:54:57 2015 +0530

    NetworkPolicyManagerService: Handling IllegalArgumentException
    
    - Avoid throwing IllegalArgumentException in case of
      MOBILE_WILDCARD and WIFI_WILDCARD Network Templates
    
    - Catching the exception to avoid the system crash in case of
      an invalid or unknown NetworkTemplate
    
    CRs-Fixed: 773212
    Change-Id: Ie782eec1373fb44601d180f732e4835fadcbddd2

commit e618bb7c8dfd38ccb640b4062f34817d4a536a4c
Author: Rakesh Pallerla <rakesh@codeaurora.org>
Date:   Fri Mar 27 19:11:56 2015 +0530

    Update Signal Strength on sim state change.
    
    Update Signal Strength on sim state change, so that when
    SIM is removed the signal icon will be updated and proper
    value is displayed on inserting other SIM
    
    Change-Id: Ie392716e0ad7783306570258fd4ec411d5dfaab6
    CRs-Fixed: 807798

commit 4bf9a39be59480169d4457c06c06d4011d8002cc
Author: Ravinder Konka <rkonka@codeaurora.org>
Date:   Thu Feb 26 17:03:48 2015 +0530

    ConnectivityService: Updating init_rwnd based on RAT class
    
    Get RAT class info and update TCP_DEFAULT_INIT_RWND accordingly
    for 2g and Non-2g Networks
    
    CRs-Fixed: 679127
    Change-Id: I1a05bac05f20a86fb8e19735b74d178d1e5ce3b0

commit 6cc441a6eeadcbebc6309a8e039315de1304a95e
Author: Rekha Kumar <rekhak@codeaurora.org>
Date:   Thu Jan 22 15:01:22 2015 -0800

    IMS-VT: Add additional error codes for upgrade downgrade
    
    -Add support to send additional error codes to UI during
     upgrade downgrade
    
    Change-Id: Id452d225098fe3bccdcd37d242985c5c761144c1
    CRs-Fixed: 769916

commit 2d4ecb4077672691767f17035e71e8bbc27911e6
Author: Evan Charlton <evanc@google.com>
Date:   Sat Nov 8 15:49:16 2014 -0800

    Apply @hide / @SystemApi to android.telecom.*
    
    Move the android.telecom.* namespace back to @hide, and also mark it
    with @SystemApi so that system-privileged apps can use them.
    
    Bug: 18302450
    Change-Id: I33ae1b9b0dfdb1c5eff51ca3c829196bcfc9411c

commit 44d38dcf1786920c23efda24513c750d216ec7c1
Author: Kiran Kelageri <kkelageri@codeaurora.org>
Date:   Wed Apr 8 14:28:03 2015 -0700

    Bluetooth: Fix for crash in multi advertiser
    
    Subsequent bt on/off's causes the callback to be rendered later than
    the actuall sequence so as to ensure the rigidity of the flow
    check is added to make sure that bluetooth is enabled before performing
    advertising.
    
    Change-Id: I1fbd35d9009abc510ac01739e37360b4eb6d3717

commit cd0e9d200e66e0ff302bb330abcd8a2c12de4cd6
Author: Tyler Gunn <tgunn@google.com>
Date:   Thu Jan 29 11:47:24 2015 -0800

    Fixing conference merge where only one party is added to conference.
    
    - Adding "onConferenceStarted" listener for Connections.
    - This is necessary so that an ImsCall can report the fact that it has
    went from being a single party call to a multiparty call. This was not
    previously necessary since the multiparty bit change would be detected
    when one of the connections being merged changed state.  Since we now must
    defer the establishment of the conference until all connections have been
    merged, we need a means of detecting when the call becomes multiparty.
    
    Bug: 18960042
    Change-Id: I3ba138cb546e3efdf89b29d6676d00257a5e00cd
    CRs-Fixed: 820312

commit 332df72f7f6065d5cbb6ee5a8696c03e00fcb6b7
Author: Brian Carlstrom <bdc@google.com>
Date:   Thu Mar 26 22:41:45 2015 -0700

    Document hprof-conv -z
    
    Bug: 18473132
    Change-Id: I3c0fcc2c15d4c590ed852f41aa4fd2a2531a6db8

commit dd4044e249983c0a80942b4ddc2799adc16ba364
Author: Muhammed Siju <msiju@codeaurora.org>
Date:   Thu Mar 12 14:26:01 2015 +0530

    IMS: Initialize audio quality with NONE instead of AMR_WB.
    
    Initial value of audio quality needs to be set to NONE to avoid
    wrong quality value during MO call setup.
    
    Change-Id: I06173abe38c9be1e9499c8c0958f985c45709f1c
    CRs-Fixed: 802704

commit ac28df132a33a01dbe4497547d2dd8a66d1016da
Author: Qiang Chen <cqiang@codeaurora.org>
Date:   Thu Mar 12 15:33:06 2015 +0800

    Disable the plus sign conversion in non-NANP system
    
    Support NANP international conversion and other telephone numbering plans.
    Return the original dial string if the phone is used in non-NANP system.
    
    CRs-Fixed: 791454
    
    Change-Id: I10d2822d0406021e6f631e722e812ad714074995

commit 1a96c2936fb4c5d2d9e18383f304f6484f51d088
Author: proDOOMman <prodoomman@gmail.com>
Date:   Fri Apr 24 14:28:31 2015 +0300

    SysUI: Add lockscreen visualizer for MSIM devices
    
    Change-Id: Iba83f34fbb731d9a13c9c3514e31537ac51cd0f2

commit d39d038d7e4d0a7c65ba01a6cd368e139f7791c7
Author: d34d <clark@cyngn.com>
Date:   Sun Apr 26 11:16:44 2015 -0700

    Themes: Pass ComposedIconInfo into createIconBitmap
    
    The majority of the parameters being passed into createIconBitmap
    were coming straight from the ComposedIconInfo so rather than pass
    them in separately we just pass in the ComposedIconInfo object.
    This will help prevent increasing the # of parameters as more
    features are added to composed icons.
    
    Change-Id: I6840db66a1369e0d75de4c662563b96dc58c34ab

commit b8a8ccfa0972fab6200329671a5742538e4cf209
Author: d34d <clark@cyngn.com>
Date:   Sun Apr 26 11:25:30 2015 -0700

    Themes: Add randomization to composed icon rotation
    
    This patch adds an addition attribute named "plusMinus" which allows
    a theme designer to specifiy a +/- variation to the angle of rotation.
    The final icon will be rotated by the angle specified +/- a random angle
    within the range specified by the value defined with "plusMinus"
    
    ex:
    <rotate angle="30" plusMinus="5" />
    
    Change-Id: I51a65c90209547417fe99b215164f8418f9f7f6b

commit 76ab7183a771330b7603b6eedf084b3aee0bb457
Author: maxwen <max.weninger@gmail.com>
Date:   Mon Apr 27 18:31:34 2015 -0700

    GlobalActions: add zen mode buttons
    
    Change-Id: Iee15bd8dc648fd465e402ba77cd0b2db61c79268
    
    Conflicts:
    	core/res/res/values/cmr_strings.xml
    	core/res/res/values/cr_symbols.xml

commit 904389c7653767690d4452ec77ba10f304b6bf4d
Author: Roman Birg <roman@cyngn.com>
Date:   Fri Aug 15 11:35:13 2014 -0700

    frameworks: add ongoing notification while collecting bug report
    
    Change-Id: I644da7046b3cbbd0ec601f0e35dfbad6adf4dcf5
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 4e8d7d3330346a31dc9b97e1340ae6cc2b4747c9
Author: Danny Baumann <dannybaumann@web.de>
Date:   Thu Apr 9 12:38:06 2015 +0200

    Re-add dump() method to TorchService.
    
    Change-Id: Ia6bb7982dac5a1f68503b64f5ac464f95fb7a103

commit 8c4dd70d17f84fa73e3cb67bd1fd7780b5b4534e
Author: Roman Birg <roman@cyngn.com>
Date:   Fri Apr 24 18:36:06 2015 -0700

    TorchService: improve state management
    
    Always dispatch state when tearing torch down.
    
    Change-Id: Ia2fbab421e552bf48f951625dd4eea48ace20363
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 1f61e763f8c09a7b48e261b9c373c73563e8e67c
Author: d34d <clark@cyngn.com>
Date:   Mon Apr 27 13:18:58 2015 -0700

    Themes: Translate before rotating composed icons
    
    Order matters.  Calling rotate before translate causes the icon to be
    rotated about a point that is not in the center.
    
    Change-Id: Ied1a0e030b39c8b6d8fb23bdbcc5a7f7928ea4a6

commit 855a0b78157dd107013adb9733f272a081f8388f
Author: Sungki Kim <skkim7@gmail.com>
Date:   Fri Apr 17 02:05:19 2015 +0900

    fix race condition.
    
    Race codition occurs after call registerApp().
    ("mAutoConnect = autoConnect;" and call mService.clientConnect(... mAutoConnect ) in onClientRegistered())
    So "mAutoConnect = autoConnect;" move to front.
    
    Change-Id: Ie1174c0f224f5084178439420b383164d22d542c

commit 10d19484ad024b523b56989964123bddc2fcd64e
Author: Frode Isaksen <fisaksex>
Date:   Fri Oct 5 11:23:44 2012 +0200

    wifi: grab MulticastLock when starting mDNS daemon
    
    Multicast DNS (mDNS) is using multicast (as the name implies), so
    grab the MulticastLock so that multicast packets are not dropped by
    the WiFi filters when screen off.
    
    Change-Id: I784bdec57f65d316c5aae960cf244a3cf80e9155
    Signed-off-by: Frode Isaksen <fisaksex@intel.com>
    Signed-off-by: Abdelmajid MLAYEH <abdelmajidx.mlayeh@intel.com>

commit 5cff4da243389335e719fc1a08dcfdedc1c1bef2
Author: Amr BEN ABDESSALEM <amrx.ben.abdessalem@intel.com>
Date:   Fri Feb 20 12:10:28 2015 +0100

    Widi disconnection should be done when powering off
    
    This patch disconnect the DUT from Widi dongle when we are powering off,
    to avoid displaying power off screen more than 10 secs on external screen
    even the device is powered off.
    
    Change-Id: I58357dd013fe0eabeddb4567bf7dfd9afab4ea7d
    Signed-off-by: Amr BEN ABDESSALEM <amrx.ben.abdessalem@intel.com>
    Signed-off-by: Matthieu MAUGER <matthieux.mauger@intel.com>
    Signed-off-by: Abdelmajid MLAYEH <abdelmajidx.mlayeh@intel.com>
    
    Conflicts:
    
    	services/core/java/com/android/server/display/WifiDisplayController.java

commit 55f9cfb1ce8ee7b600244b911d84f340424c9b67
Author: daegeun.song <daegeun.song@lge.com>
Date:   Tue Oct 7 13:24:35 2014 +0900

    Reduce sscanf times for optimization
    
    Reduce sscanf times for optimization.
    
    Signed-off-by: Daegeun Song <daegeun.song@lge.com>
    Change-Id: I1881dcb70308fc3a43b2fe19ca8df51d688ffa69

commit 974e7b634df736a726f88b29c5318923a7c685dd
Author: jinchul.kim <jinchul.kim@lge.com>
Date:   Wed Apr 8 20:19:25 2015 +0900

    Trim task thumbnail within MAX_RECENT_BITMAPS.
    
    Task thumbnails can be hold as much as length of mRecentTasks because
    freeLastThumbnail only works when any task is added and it might cause
    the system heavy.
    
    Free lastThumbnail when it reuses exist taskRecord also to keep
    thumbnails within MAX_RECENT_BITMAPS.
    
    Change-Id: I932a16c20acb3d8ead2a238ba221a0fa19484b9a

commit 571c7ed0cf23764e76a41b321ca3ff91103b8da3
Author: Lars Greiss <kufikugel@googlemail.com>
Date:   Tue Apr 28 03:01:41 2015 -0700

    fb: TRDS 5.0 (1/4)
    
    patchset: add holodark resources
    
    patchset: add to slim actions
    
    patchset: import Toast library in Action.java
    
    patchset: some tweaks and fixes
    
    patchset: change auto detect light conditions method
    
    patchset: fix possible UI freeze on auto mode change
    
    patchset: import ServiceManager library into uimodemanagerservice
    
    patchset: fix aapt shit
    
    patchset: fix context in UiModeManagerService?
    
    patchset: set mContext to BroadcastReceiver's context,
            add toasts to debug light sensor stuff
    
    patchset: adjust DARK_CONDITION value
    
    patchset: clean up toasts
    
    patchset: fix NPE in Resources.java?
    
    PS20: update BridgePowerManager to fix SDK build
    
    PS21: revert to original BridgePowerManager (if building SDK tools,
            need to use patchset 20 or it will error out)
    
    PS22: more debugging toasts grrrrr
    
    PS23: change holodark to darktheme, hololight to lighttheme.
            remove holodark resources.
    
    PS24: add darktheme resources.
    
    PS26: qs tile
    
    PS27: reset theme mode on longpress qs tile
    
    PS: fix qs icon
    
    CyanideL: Fix up to work ALONGSIDE theme engine
    Change-Id: Ic88838247c47d2a92b55d1cb1b00330f2d62fb88
    
    Conflicts:
    	core/java/android/provider/Settings.java
    	core/res/res/values/cr_symbols.xml

commit caa3276748106ddd69652bdc9ebcae4bb32e1fb2
Author: rogersb11 <brettrogers11@gmail.com>
Date:   Thu Apr 23 03:43:57 2015 -0400

    Update trds colors
    
    Change-Id: I3f97326752d71d142212a99fcc220975032654d0

commit 2247cbf697d4d216c34949ecfec500f84041cea4
Author: Lars Greiss <kufikugel@googlemail.com>
Date:   Tue Apr 28 03:03:32 2015 -0700

    Frameworks: SlimPie give user ability to reduce trigger heights if IME keyboard shows (1/2)
    
    Add a user option to reduce left and right trigger of SlimPie if keyboard shows up
    (especially usefull for swipe keyboard which most keyboards are nowadays). Enabled
    by default user can disable it in settings.
    
    Change-Id: Idc985ebc1d2b14706c26c5c69894b4393b5d57ff
    
    Conflicts:
    	core/java/android/provider/Settings.java

commit cc55fe45881125d3471053e0a7c13b39158b6282
Author: Lokesh Chamane <lokesh.c703@gmail.com>
Date:   Tue Apr 28 03:05:19 2015 -0700

    SlimPIE: Configurable sensitivity [1/2]
    
    Change-Id: I636bbbf3a63104625e1cf4698392a480c1f9458a
    Signed-off-by: Lokesh Chamane <lokesh.c703@gmail.com>
    
    Conflicts:
    	core/java/android/provider/Settings.java

commit 3da027ea507b0f22e902d04d8458e87cd4c04463
Author: Richard MacGregor <rmacgregor@cyngn.com>
Date:   Wed Apr 15 17:13:40 2015 -0700

    Apply sounds on theme update
    
    Add content observer so themeservice knows whether ringtone was
    changed outside of themes.
    
    Change-Id: I83a5dff8e9574019f4d1a5bd58368b0ec3c09c88

commit f9d10ddb15a427277e14abecee8ee32c35bb2d71
Author: Danny Baumann <dannybaumann@web.de>
Date:   Tue Apr 28 10:55:15 2015 +0200

    Unset frame listener before tearing down GLThreadManager.
    
    Otherwise might lead to messages being delivered to the then dead
    mGLHandlerThread via RequestThreadManager.mPreviewCallback ->
    GLThreadManager.queueNewFrame().
    
    Change-Id: I60001149787c584bfee88c961f1e07cdb8cf3927

commit 3e66f1cbb8f3e82ff5184a2dac7fa485db014563
Author: Roman Birg <roman@cyngn.com>
Date:   Wed Apr 15 09:19:09 2015 -0700

    Torch: remind user flashlight is still on
    
    Post a notification which informs the user the flashlight is still
    enabled. But only do this when the user turns the screen off *while* the
    flashlight is still on, so they see it next time they use the device.
    Tapping on the notification will disable the flashlight.
    
    Change-Id: I3689ff6498b97b813ccc10dc7dca3527fc8455aa
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit d08ecfcf1eb599e873d35522bc2af3ef7a5abbea
Author: Taiju Tsuiki <tzik@google.com>
Date:   Wed Apr 22 16:59:00 2015 +0900

    Fix NullPointerException in Bundle#hasFileDescriptors
    
    Add null check for array elements in Bundle#hasFileDescriptors to avoid NPE on
    null valued array.
    
    Change-Id: Ic6ef8864ca6add023c7a69ba3c9474b0f6291723

commit 0c8b2cdc52629fadf92a6fe168c6e234aecb2df6
Author: Taiju Tsuiki <tzik@google.com>
Date:   Tue Apr 28 13:36:15 2015 +0900

    Fix NPE in Bundle#hasFileDescriptor on null-valued SparseArray
    
    Add a null check for each values of SparseArray in Bundle#hasFileDescriptor
    to avoid NullPointerException.
    
    Change-Id: I43ecc01f2759ccbe85b902fa118d55cb74ebf38b

commit d0481e081e03120a0ad2e22aca8fab0a2a418e2e
Author: Henrik Engström <henrik.engstrom@sonymobile.com>
Date:   Tue Apr 24 15:30:19 2012 +0200

    Fix for infinite loop in RemoteViewsAdapter
    
    This patch fixes an error in RemoteViewsAdapter when there is only one
    view in the cache, and it is bigger than the cache size threshold. This
    would cause the cleanup of the cache to get stuck in an infinite loop
    while holding the mCache lock that is also needed by for example
    getView which is called on the UI thread, leading to ANRs. This patch
    breaks the loop when it sees that it can not remove the next view up
    for removal.
    
    Change-Id: I331259bb10eae9fe91e5112102e08f49cc078a1b

commit 9f42bcf59a548c15ee6dde69f5048acffce5f336
Author: UtkarshGupta <utkarsh.eminem@gmail.com>
Date:   Wed Apr 29 19:40:49 2015 -0700

    [1/2] Battery light: 100% charged level
    
    Conflicts:
    	core/java/android/provider/Settings.java

commit 3f75cb94bf0f461246b4c59e7bd26e325cc674a1
Author: Danny Baumann <dannybaumann@web.de>
Date:   Tue Apr 28 12:46:41 2015 +0200

    Fix fetching application context for ThemedUiContext.
    
    Change-Id: I7719fc8823fef93556f5a9ab088a77b73cf7eeff
    
    Patchset: 3
    http://review.cyanogenmod.org/#/c/96386/

commit a0422c3e3e76956627dd4dd2626dca3d8b5b634f
Author: Lars Greiss <kufikugel@googlemail.com>
Date:   Wed Apr 29 19:54:37 2015 -0700

    Frameworks: Add ability to control default value of DOZE_ENABLED
    
    Devices can enable the doze feature. Devices without AMODLED screens can use it
    but it will use then of course more battery. This devices should disable this feature
    by default and let the user decide to turn it on.
    
    to change the default behaviour add into device overlay
    
    config_doze_enabled_by_default and set it to false
    
    Change-Id: I1afbf1d09fa0d7e68aea40f2f165a72ff34d0040
    
    Conflicts:
    	core/res/res/values/cmr_config.xml
    	core/res/res/values/cr_symbols.xml

commit 6cf375416da5cb2b31f78c1f5c1d568e50293755
Author: Mikael Gullstrand <mikael.gullstrand@sonymobile.com>
Date:   Tue Jul 9 14:41:28 2013 +0200

    Context leaks in EditText causes out of memory
    
    In android.widget.Editor, Blink runnables can be posted even if
    the related TextView is not attached to a window. If a message has
    been posted to the Blink message queue and the run method of
    the Blink runnable has started executing, the removeCallbacks call
    in onDetachFromWindow method is not enough to abort the execution
    of the Blink runnable. This results in a memory leak when
    the activity is destroyed.
    
    The solution is to cancel the execution of the Blink runnable by
    calling the suspendBlink method from onDetachFromWindow method.
    Hence the Blink thread will halt, and the referenced context can
    be released by GC when the activity is destroyed. Also adding
    a corresponding resumeBlink method call in onAttachedToWindow
    to start executing the Blink runnable.
    
    Change-Id: Icb26c9c947b3cc1158f7629ae35d7b4e42b80f17

commit 04878974c6d62a1eea4423ef5597c8acf82ca778
Author: Lin Ma <lma@cyngn.com>
Date:   Wed Mar 25 17:44:52 2015 -0700

    Fix ro.telephony.default_network setting parsing
    
    * The code that parses ro.telephony.default_network is broken,
    instead of reading numbers separate by comma, it reads the first
    number and replicates it for other slots. Settings like "8,1" will
    be written to the db as "8,8"
    
    Conflicts:
    	packages/SettingsProvider/src/com/android/providers/settings/DatabaseHelper.java
    
    Change-Id: I6b77000e00ada02ec89b09c752a9b337a6a8182b
    
    Patchset: 2
    http://review.cyanogenmod.org/#/c/96401/

commit 76921219c7d8d3267a02df1aa05424c93b966b7f
Author: Patrick Lower <devvortex@gmail.com>
Date:   Wed Apr 29 15:25:46 2015 -0400

    MMS (change 1 of 2): Add DATA_PROFILE_MMS constant = 5 to RILConstants.
    
    Some carriers require a separate apn just for MMS.  RIL needs to be aware of this differnt type in order to set the correct network interface information and not interfere with the existing data connection.
    
    Change (2 of 2) 96584
    Change-Id: I793982c1f2032e98a069ff86a748301af4ff6377
    
    Patchset: 2
    http://review.cyanogenmod.org/#/c/96582/

commit c1dbd2756034df84e3e3341e8bb035c431d2673a
Author: Danny Baumann <dannybaumann@web.de>
Date:   Thu Apr 23 09:28:43 2015 +0200

    Clean up keyguard carrier text handling.
    
    Return to AOSP code, which both simplifies the code and fixes the
    left alignment.
    
    Change-Id: I1b8974948ace3d55ff92eceace7ea22b715d010d
    
    Patchset: 1
    http://review.cyanogenmod.org/#/c/95932/

commit 50d446011731fa572a136f77339373eb89b91a80
Author: dankoman <dankoman30@gmail.com>
Date:   Fri Mar 20 16:54:05 2015 +0100

    slimseekbarpreference: set monitorbox text as string
    
    setting as integer was trying to reference a resId,
            so integer needs to be converted to string
            before setting monitorbox text.
    Change-Id: I085d49240be30e12475db7d88d3b2154d2e65ffd

commit 35e8ce98ee63ed8dd1555cb7da824159b64a7449
Author: d34d <clark@cyngn.com>
Date:   Wed Apr 29 09:04:47 2015 -0700

    Themes: include new icon features in shouldComposeIcon()
    
    Change-Id: I509ae1989fe1ec701cec7bc6ead78ab4e69bd64d

commit 846813104e4ea9b03f03fc0c3f9a010753f1646b
Author: Altaf-Mahdi <altaf.mahdi@gmail.com>
Date:   Wed Apr 15 19:04:19 2015 +0100

    Base: enable/disable doze through Profiles (1/2)
    
    Change-Id: I37a3613a7e4a8d54b43ec9336c4aebc5a92d8d77

commit 82aab46c1b3cffc25bc3649a1c9f2496ad1a8e14
Author: Altaf-Mahdi <altaf.mahdi@gmail.com>
Date:   Thu Apr 30 13:55:58 2015 -0700

    Base: Add a controller for in-call proximity sensor (1/3)
    
    Change-Id: Icd17599ef3e0c45ee10fede7d663ea9a30446257
    
    Conflicts:
    	core/java/android/provider/Settings.java

commit 0b0b9b73abe913b54159286f28dbc07e93138328
Author: longyu.huang <longyu.huang2014@gmail.com>
Date:   Thu Apr 23 04:17:14 2015 -0700

    optimize wallpaper load,avoid show black wallpaper.
    
    [Preconditions]
    open auto-rotate
    
    [Procedures]
    1.enter Contacts app, and rotate 90 degrees to the right
    2.press power key to lock screen,and unlock
    3.rotare 90 degrees to the left and exit Contacts app
    4.the wallpaper will be black first,then show the really wallpaper.
    
    Change-Id: Ia8f77b9a685c49cfc0a33e661ef073d90b8b363c

commit 5bf6f6fda1bc09836ea858c76116da142373b390
Author: Roman Birg <roman@cyngn.com>
Date:   Thu Apr 30 11:44:57 2015 -0700

    SystemUI: bluetooth tile: fix disconnect action
    
    Change-Id: I3858dae5539baeb6e70220e39af9cc22134280c9
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 84512731ebca12d01e4c585ca7a9f7a9fd9bd5d7
Author: Apoorv Raghuvanshi <apoorvr@codeaurora.org>
Date:   Mon Mar 30 17:58:55 2015 -0700

    audio: Playback over USB DAC connected before boot
    
    Playback over USB DAC does not work if USB cable from MTP
    to USB DAC is connected before phone bootup. Fix by making
    sure if USB is connected then picking the same
    
    Change-Id: Ifb10e794ed7f21bcf26349440d2c2a9baf7a28aa
    CRs-Fixed:803353

commit ab858c8b6b01f6468cd1591ce8569f4a0466b562
Author: Ravinder Konka <rkonka@codeaurora.org>
Date:   Tue Dec 30 16:57:36 2014 +0530

    Tethering: Set sys.usb.tethering to true on Tethering
    
    Set the system Property "sys.usb.tethering" to true when
    tethering is enabled on UI
    
    Change-Id: I805a38b2d3ed055a562298d71f33fd5030b3a4a0

commit 0e988e896ed37de936b094bc6303d1f1777f18e2
Author: kaiyiz <kaiyiz@codeaurora.org>
Date:   Mon Jan 5 10:44:19 2015 +0800

    Widget: Catch null point exception in AbsListViewAutoScroller
    
    The first view of AbsListView is null, so there is a NullPointerException
    happen.
    
    Add a judgement for the first view of AbsListView.
    
    CRs-Fixed: 776294
    
    Change-Id: I7e25d1430b1bab0cff313492163a419fbf5960b5

commit c3de0de6ada8e078d7229aec1a4f0a397f4b7eb7
Author: kaiyiz <kaiyiz@codeaurora.org>
Date:   Mon Feb 9 14:08:14 2015 +0800

    WindowManager: Disable rotation for BootAnimation screen
    
    BootAnimation screen is not rotated when device bootup or shutdown.
    And still should not be rotated when device doing factory data
    reseting. Otherwise BootAnimation layer would only cover the left
    part of the screen and display error.
    
    Change-Id: I79515dcc87965257e1773142138a84449fb711e4
    CRs-Fixed: 784522

commit ba19da1b8c46ad287afa263701cc8b2b46705825
Author: Kun Liang <kunliang@codeaurora.org>
Date:   Tue Jan 6 15:21:04 2015 +0800

    AppOps: allow MEDIA_RW uid to start activity
    
    Sdcard daemon, which is running with MEDIA_RW uid, need start activity
    to show dialog to users when apps try to access protected files.
    
    Change-Id: Iac1efb862e9579d3f59786c57cf18fe6518ce87b

commit d2a5e2f6bfc6297a419fd113f8adcdcbdd925807
Author: kaiyiz <kaiyiz@codeaurora.org>
Date:   Wed Feb 11 11:40:51 2015 +0800

    RP: Notification and ringtone can't be overlaid by carrier
    
    There are some logic error for ringtone and notification
    overlay when sound customized. Reconstruct these code to
    make it overlay the right ringtone and notification.
    
    Change-Id: I0fd0abfe833c7920bf3ce6829998b92644eae48c
    CRs-Fixed: 761741

commit 7cba896938a0984dd673ecf4581963a1c3d4f898
Author: kaiyiz <kaiyiz@codeaurora.org>
Date:   Mon Jan 19 10:26:05 2015 +0800

    MMS: Fix the edit options menu disappear after click edit button
    
    It should not check if the PopupWindow is not showing before hide
    the PopupWindow.
    
    It should check if the PopupWindow is showing before hide PopupWindow.
    
    CRs-Fixed: 778105
    
    Change-Id: I80fe49c270ca3ba4d6c22c6aa32408826ff3ac5c

commit c338a9928cf72618084d8a6ee61cf3f0ba22088c
Author: Matt Garnes <matt@cyngn.com>
Date:   Wed Feb 11 18:37:57 2015 -0800

    Do not play the default ringtone if it cannot be retrieved.
    
    In performAuditoryFeedbackForAccessibilityIfNeed() if the default
    ringtone cannot be retrieved, do not try to set the stream or play it.
    
    TODO: Find the invalid condition that caused this scenario to occur in the first place.
    
    Change-Id: I79d00e016fc07e66f32723c49090a2098163f905

commit c66239ee7f298b93b97cb257ca2ff25e0f01f21c
Author: Pan Fang <fangpan@codeaurora.org>
Date:   Thu Mar 5 15:40:47 2015 +0800

     WindowManager: remove freezing window to fix UI freezing issue
    
     In some corner case, some window is at exiting state, but can't be
     removed. This will result the windownmanger fall into freezing state.
     The fix will remove this exiting window when encounter this case.
    
    CRs-Fixed: 803491
    Change-Id: I8ba72ab0566e9d13a0405be1fa4472f826d0af50

commit 896f7498c218239e465248ed62af43d148d14c9a
Author: laufersteppenwolf <laufersteppenwolf@gmail.com>
Date:   Mon Jan 5 21:33:19 2015 +0100

    Fix GPS for old GPS HALs
    
    Some old GPS HALs like the one on the Optimus 4x HD are broken without this
    and can also cause bootloops (like on the 4x HD).
    To enable this just add the following to your config.xml overlay:
    
    <bool name="config_legacyGpsHAL">true</bool>
    
    Change-Id: I3108d9f1baf728132f048ddba846d3db96173ec7

commit ecfcaf903552b3fb17b4800940bdba6aaa903df3
Author: riddle_hsu <riddle_hsu@htc.com>
Date:   Thu Mar 19 01:11:55 2015 +0800

    Fix no vibration during shutdown.
    
    In ShutdownThread:rebootOrShutdown, the vibrator is created
    by "new SystemVibrator()" which will use default constructor
    of Vibrator.
    
    And because system server is not bound application,
    ActivityThread.currentPackageName will be null.
    Then the member mPackageName of Vibrator is null.
    
    When doing vibration:
    VibratorService.startVibrationLocked
     -> mAppOpsService.startOperation
     -> getOpsLocked (null package will get null op)
     -> return MODE_ERRORED
     -> no vibration
    
    https://code.google.com/p/android/issues/detail?id=160830
    
    Pass null context in SystemServer.performPendingShutdown
    because vibrator service is not ready, and from the call
    sequence, there is no available context to use.
    
    Change-Id: I3e0175ba6dc2e1a92787873eda4461fba6e89783

commit 973c4fea609a447146361464f308cdee7c0f4785
Author: Alan Viverette <alanv@google.com>
Date:   Tue Apr 28 17:30:04 2015 -0700

    Adjust display inversion matrix to account for luminance
    
    Bug: 20346301
    Change-Id: I10633705f2bfddbdeec063f9489a4f8679b9e8ee
    (cherry picked from commit 6437518061fc8718590e0272ed17ea64710d2299)

project frameworks/native/
commit 9c16578a0e20a323812c476b3004bd74fc0317a2
Merge: 521ce7b f22a457
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 17:49:46 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

commit 5ac19fa6c9a52bc1a97c66feda0f84e2ccd92017
Author: Lars Greiss <kufikugel@googlemail.com>
Date:   Sat Dec 14 02:58:19 2013 +0100

    native: TRDS 5.0 (2/4)
    
    Change-Id: Ibc5aaec5661455477815043440fae86052a395ce

project frameworks/opt/telephony/
commit 2e374b88cba1803edcb540e5c64f50aa468cc573
Author: Ricardo Cerqueira <ricardo@cyngn.com>
Date:   Fri Apr 24 00:14:01 2015 +0100

    SubscriptionController: getPhoneId() should never return negative values
    
    Most places dealing with getPhoneId() check for negative returns and use
    zero if it happens. Instead of doing that, when dealing with negative subIds
    generate positive slot identifiers by replicating the logic from changes
    I91d99c98cff9b6fd484d4972b5461098bba23ba2 and Id013b2673645b63db8c96660e5a9446347a3e2e5
    
    Change-Id: I4577764298cd53199d036d40b58b6c9490c2bacb

commit ed68de07c09286673b34346e0e13c98a9a51f095
Author: Danny Baumann <dannybaumann@web.de>
Date:   Thu Apr 23 16:49:21 2015 +0200

    Don't use invalid phone IDs as index.
    
    phoneId can be -1 via this path, triggered via SimBootReceiver:
    java.lang.Throwable
         at com.android.internal.telephony.dataconnection.DctController$SwitchInfo.<init>(DctController.java:743)
         at com.android.internal.telephony.dataconnection.DctController.setDefaultDataSubId(DctController.java:781)
         at com.android.internal.telephony.SubscriptionController.setDefaultDataSubId(SubscriptionController.java:1443)
         at com.android.internal.telephony.SubscriptionController.clearDefaultsForInactiveSubIds(SubscriptionController.java:1533)
         at com.android.internal.telephony.ISub$Stub.onTransact(ISub.java:307)
         at android.os.Binder.execTransact(Binder.java:446
    
    Change-Id: Idf050fe5fff9b24cdbf890d0abc12d52fba21b3f

commit d4df7d205703b8a5a70721118d058ff94854ab71
Merge: 2838601 ed68de0
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 17:51:30 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

commit d61a1880e506cb7b97864a75c9f906298f9c8902
Author: Dan Pasanen <dan.pasanen@gmail.com>
Date:   Wed Dec 31 18:21:00 2014 -0800

    CdmaLteServiceStateTracker: allow forcing reading eri from xml
    
    * Some devices rely on eri.xml for their cdma text display and
      must be forced to use it. Not reading from eri.xml results in
      weird carrier display like NAM1 when on a cdma data network
    
    Change-Id: I73cbedafda912e52817d57e791bf57f8fb32ab48

commit ce6bd446dfdb2dec08629b55d7b6507d5168da06
Merge: d4df7d2 d61a188
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 19:22:33 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

commit 6d2524626b7e006425ed23d757b4a6b11cc631f2
Author: maxwen <max.weninger@gmail.com>
Date:   Wed Apr 15 23:30:24 2015 +0200

    telephony: kill IccSmsInterfaceManager log spam
    
    Change-Id: I11aba1edb5af50ccd769f6102875ab09e2895d5f

commit e2199ed78f186bf15f6445e2ea945f3a3705daf9
Author: Patrick Lower <devvortex@gmail.com>
Date:   Wed Apr 29 15:31:29 2015 -0400

    MMS (change 2 of 2): Update apnProfileID for MMS only apn.
    
    Depends on: http://review.cyanogenmod.org/#/c/96582/
    
    Change-Id: I3dfaddc6d4a0ee581f98e9290d4593b79cd3b2c6
    
    Patchset: 2
    http://review.cyanogenmod.org/#/c/96584/

project hardware/qcom/audio-caf/msm8974/
commit 24c0fe3a452b107765867619276bbddbc3a5b5dd
Author: Weiyin Jiang <wjiang@codeaurora.org>
Date:   Tue Apr 7 11:36:35 2015 +0800

    post_proc: remove unnecessary command size check
    
    Up bound check for command size of EFFECT_CMD_SET_PARAM is not
    applicable for DSP effect bundle. Remove the check to avoid parameter
    not taking effect.
    
    Change-Id: I7e8f73377699f11bdc1f62a05f6bea03c9c24151
    CRs-Fixed: 816053

project kernel/samsung/hlte/
commit da9dae79da954082cca3a62b6b55db334da9d0d7
Author: Steve Kondik <steve@cyngn.com>
Date:   Mon Feb 9 12:40:00 2015 +0000

    video: mdss: Color temperature interface using PCC
     * MDSS5 supports Polynomial Color Correction. Use this to implement
       a simple sysfs API for adjusting RGB scaling values. This can be
       used to implement color temperature and other controls.
     * Why use this when we have KCAL? This code is dead simple, the
       interface is in the right place, and it allows for 128X accuracy.
    
    Change-Id: Ib848d6c9dbdf41f61cc7539a61138d6632ceba94

commit cf23d320e981fdad971a8dc644e8ffa63c40483e
Author: Erik Kline <ek@google.com>
Date:   Tue Oct 28 18:11:14 2014 +0900

    net: ipv6: Add a sysctl to make optimistic addresses useful candidates
    
    Add a sysctl that causes an interface's optimistic addresses
    to be considered equivalent to other non-deprecated addresses
    for source address selection purposes.  Preferred addresses
    will still take precedence over optimistic addresses, subject
    to other ranking in the source address selection algorithm.
    
    This is useful where different interfaces are connected to
    different networks from different ISPs (e.g., a cell network
    and a home wifi network).
    
    The current behaviour complies with RFC 3484/6724, and it
    makes sense if the host has only one interface, or has
    multiple interfaces on the same network (same or cooperating
    administrative domain(s), but not in the multiple distinct
    networks case.
    
    For example, if a mobile device has an IPv6 address on an LTE
    network and then connects to IPv6-enabled wifi, while the wifi
    IPv6 address is undergoing DAD, IPv6 connections will try use
    the wifi default route with the LTE IPv6 address, and will get
    stuck until they time out.
    
    Also, because optimistic nodes can receive frames, issue
    an RTM_NEWADDR as soon as DAD starts (with the IFA_F_OPTIMSTIC
    flag appropriately set).  A second RTM_NEWADDR is sent if DAD
    completes (the address flags have changed), otherwise an
    RTM_DELADDR is sent.
    
    Also: add an entry in ip-sysctl.txt for optimistic_dad.
    
    [backport of net-next 7fd2561e4ebdd070ebba6d3326c4c5b13942323f]
    
    Signed-off-by: Erik Kline <ek@google.com>
    Acked-by: Lorenzo Colitti <lorenzo@google.com>
    Acked-by: Hannes Frederic Sowa <hannes@stressinduktion.org>
    Signed-off-by: David S. Miller <davem@davemloft.net>
    Bug: 17769720
    Change-Id: I440a9b8c788db6767d191bbebfd2dff481aa9e0d

commit 933c2daa05d19ff5e31bba4f569b49c43eaed5f8
Author: Erik Kline <ek@google.com>
Date:   Fri Dec 5 19:45:10 2014 +0900

    net: ipv6: allow choosing optimistic addresses with use_optimistic
    
    The use_optimistic sysctl makes optimistic IPv6 addresses
    equivalent to preferred addresses for source address selection
    (e.g., when calling connect()), but it does not allow an
    application to bind to optimistic addresses. This behaviour is
    inconsistent - for example, it doesn't make sense for bind() to
    an optimistic address fail with EADDRNOTAVAIL, but connect() to
    choose that address outgoing address on the same socket.
    
    Bug: 17769720
    Bug: 18609055
    Change-Id: I9de0d6c92ac45e29d28e318ac626c71806666f13
    Signed-off-by: Erik Kline <ek@google.com>
    Signed-off-by: Lorenzo Colitti <lorenzo@google.com>

project packages/apps/Browser/
commit 45284de420f2674b7a28cebaf02b6e5880050f22
Merge: dd822c5 9d321ea
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:04:18 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

project packages/apps/CMFileManager/
commit c6a778c871ee092117305115c93bc93117c34ddd
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:13:51 2015 +0300

    Automatic translation import
    
    Change-Id: I4d2b17d0f4ec00915ff36255a8ccfce547a88db1

project packages/apps/CMWallpapers/
commit c0019e29644978f4aec5954d6aaa22cc0e5cbb10
Author: d34d <clark@cyngn.com>
Date:   Fri Apr 24 16:54:57 2015 -0700

    Use the new partner customization to load wallpapers
    
    Lollipop introduced the ability to load 3rd party wallpapers provided
    that those apks are system apps.  All that is required is to declare
    a receiver in the manifest that handles the action
    com.android.launcher3.action.PARTNER_CUSTOMIZATION.  This receiver
    is never launched so there is no need to have a source file for it.
    
    Change-Id: I967b75f30785710e59926783dc018a20b0fd8625

project packages/apps/Calculator/
commit 6e66a7eeed94b273458cfce555ce3b1a342645cd
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:13:37 2015 +0300

    Automatic translation import
    
    Change-Id: Ia630bac5587cff543068ded2ae81c808f30beb4c

project packages/apps/Calendar/
commit b653503bf591b0d825bcdd7b8e77a7af002a7ef0
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:13:45 2015 +0300

    Automatic translation import
    
    Change-Id: Ic0945f6101b2698207c51c570da842b9bad39adb

project packages/apps/Contacts/
commit 54348d9e06bfdaa2b5ae6956f50e66bb9222a21f
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:14:00 2015 +0300

    Automatic translation import
    
    Change-Id: I13fb65b5f9207adcffd395adc3ac65e56830abbe

project packages/apps/ContactsCommon/
commit ec58d211e65517c87e2d2855ba8bed94e0727171
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:14:05 2015 +0300

    Automatic translation import
    
    Change-Id: I7eca9579f52dd15c7abc31d22532a2f74381e464

project packages/apps/DeskClock/
commit 5ab226efd7a0e9bc5a2d9942e4f832c37192abc4
Author: Martin Brabham <optedoblivion@cyngn.com>
Date:   Fri Apr 24 13:56:00 2015 -0700

    Make new menu entry to link to cLock widget settings.
    
    Change-Id: I13ca3156c34eccdd8f60d8585281ae0585aac58e

project packages/apps/Dialer/
commit 8d9ceaf3d2cdf48bfb0779df4fc6a959db9f7f8b
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:14:10 2015 +0300

    Automatic translation import
    
    Change-Id: I124c3c0a1cc4b3c8822438729137ad327f44a033

commit c2b914999e19b0bd4758d09152ea3a9bb533d9d6
Author: NBruderman <nbruderman@gmail.com>
Date:   Mon Mar 2 20:27:11 2015 +0200

    Dialer: Whitelist few EU countries for call recording
    
    All entries to this list patch should state the country being modified
    and
    provide a URL reference (either government law, precedent or similar).
    
    A disclaimer item will also be added to the InCallUI view for the user
    to
    acknowledge that it is their responsibility to conduct/maintain and use
    recordings in conjunction with their respective country/region's laws.
    
    Change-Id: Id6aa02447e9e8b6520cbe7c6eada7df333ee42a0

commit 8951136add43f4471765d7d5a59556a2e19cea6d
Merge: 2c62386 8d9ceaf
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:06:35 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

commit 0c1b9eaef7715981b11cfb816c1a50e716727672
Merge: 8951136 c2b9149
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 19:28:07 2015 -0700

    Merge remote-tracking branch 'upstream/cm-12.1' into cm-12.1

project packages/apps/Eleven/
commit 469d0e8ec3757356ea608393575db016448b0678
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:14:16 2015 +0300

    Automatic translation import
    
    Change-Id: If11d181c630d1439723ccdf38d2af70a01d1bcd9

project packages/apps/Email/
commit f325778282c882c6fa8246adfa217416803b9704
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:14:22 2015 +0300

    Automatic translation import
    
    Change-Id: Id354731aa653029aa9cce6f75489559f2c9bbaf7

commit 108dfdce54f86529bdd75969b8fcc11bf77ad155
Merge: 3080c4d f325778
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:06:56 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

project packages/apps/Exchange/
commit 6a42f289648b64a69e7505e1e4982cd382a509bc
Merge: ff98419 8d5fbea
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:07:13 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

project packages/apps/InCallUI/
commit c7f41012299c5f231e65c8d1e8f32549dfc5e992
Author: Roman Birg <roman@cyngn.com>
Date:   Wed Apr 15 10:07:28 2015 -0700

    InCallUI: show legal warning on first call record
    
    Change-Id: Ia404652b2e20177426c03c053ea8c4cffd1db52d
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 54cc6d4fe8109beb80a10af9ac3eb53b117bcd02
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:14:33 2015 +0300

    Automatic translation import
    
    Change-Id: Id588cd68a13602a910b8eeb24be163d07c42f46c

commit 8381be34cea4dd29b73b4e1964d5e276ac943d31
Merge: 9612017 54cc6d4
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:07:55 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

commit b3e301024b62373bb57e503f25d27e0d2fcc83c2
Author: Altaf-Mahdi <altaf.mahdi@gmail.com>
Date:   Tue Apr 28 20:40:29 2015 +0100

    InCallUI: Add a controller for in-call proximity sensor (2/3)
    
    follow up to this patch
    https://github.com/Euphoria-OS/android_packages_apps_InCallUI/commit/9cc23a9201b7580b0cbb6018ba62b0b06b8f1651
    
    Change-Id: If3d581486c5776b1d030e1087bdf664be468115a

commit 068cee8dcad16d63bb000bef0534d40cd5309f0c
Author: Yorke Lee <yorkelee@google.com>
Date:   Mon Mar 30 12:31:19 2015 -0700

    Don't hide end call button until call is disconnected
    
    Currently, the end call button is hidden the moment the user
    initates a hangup. In the event that the call is not actually
    disconnected, the UI is stuck in a "Hanging up" state that is
    unresponsive
    
    For the majority of calls that disconnect correctly, there should
    be no user-perceptible difference in behavior. For calls that are
    not disconnected correctly, the end call button will remain showing
    so that hangup commands can continue to be sent that will eventually
    disconnect the call correctly.
    
    Bug: 19933863
    Change-Id: I2ff2018d7d229615f5f57c599f74954ec7492f6b

project packages/apps/KernelAdiutor/
commit 84102f14a3b26d31e868e49f9a9f0faa0136be4c
Author: Willi Ye <williye97@gmail.com>
Date:   Thu Apr 23 21:30:45 2015 +0200

    Revamp the FABs
    
    Conflicts:
    	app/src/main/java/com/grarak/kerneladiutor/fragments/PathReaderFragment.java
    	app/src/main/java/com/grarak/kerneladiutor/fragments/RecyclerViewFragment.java
    	app/src/main/java/com/grarak/kerneladiutor/fragments/tools/BuildpropFragment.java
    	app/src/main/java/com/grarak/kerneladiutor/fragments/tools/RecoveryFragment.java
    	app/src/main/res/values/arrays.xml
    
    Change-Id: I2b082b2525fc608879272f7e355627b521d1b804

commit 9977bffc1720345a22b71c2394f89332329e242a
Author: Willi Ye <williye97@gmail.com>
Date:   Thu Apr 23 21:35:57 2015 +0200

    version 0.9.2.1 beta

commit 6ba3d0c08bfe5f396d92d3c9be981c241e10c084
Author: Willi Ye <williye97@gmail.com>
Date:   Thu Apr 23 23:25:35 2015 +0200

    Fix applyonboot in ViewPagerFragment
    and hide applyonboot when scrolling
    
    Conflicts:
    	app/src/main/java/com/grarak/kerneladiutor/fragments/RecyclerViewFragment.java
    	app/src/main/java/com/grarak/kerneladiutor/fragments/kernel/CPUFragment.java
    	app/src/main/java/com/grarak/kerneladiutor/fragments/kernel/IOFragment.java
    
    Change-Id: Ice177c6708aa2f32e29225917e642e87dc840297

commit 71e1697fb3d1e0a26b32c4533b6a317d658707e8
Author: Willi Ye <williye97@gmail.com>
Date:   Thu Apr 23 23:28:02 2015 +0200

    version 0.9.2.1.1 beta

commit 0dc85a721c42e8674c650d4a2f1155bb60ffc5af
Author: Willi Ye <williye97@gmail.com>
Date:   Thu Apr 23 23:31:38 2015 +0200

    Import translations from crowdin

commit eff49242af7c075715ef7c027c43eb01844588d6
Author: Willi Ye <williye97@gmail.com>
Date:   Thu Apr 23 23:36:05 2015 +0200

    Remove unnecessary logging

commit 6866bf649604796d589ea908f9026e1a28b3ce5e
Author: Willi Ye <williye97@gmail.com>
Date:   Thu Apr 23 23:50:02 2015 +0200

    Make sure database is not null

commit dd9459e8b9514a322759b9a39a82411b94c8c90d
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 02:46:14 2015 +0200

    Add own file browser
    
    Conflicts:
    	app/src/main/java/com/grarak/kerneladiutor/fragments/tools/RecoveryFragment.java
    
    Change-Id: I89e8bea17129a0d22ff1f853ee7601a2321714ce

commit 2bb1801eff346858200091dfe93fa2e9fc59d8f2
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 02:49:04 2015 +0200

    version 0.9.2.2 beta
    
    Conflicts:
    	app/app.iml
    
    Change-Id: I1ed247f7bb426acbc91f41f3e131faacc372a55c

commit 7a3afd3c269c6bdb95d6e372db2f1c1887349795
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Apr 25 15:12:53 2015 +0200

    libs: Update support libraries to 22.1.1
    
    Change-Id: If3fc9fcae4675a787ddbc1e4dc84169e01a8a42d

commit 78deb67ece164017f137897b69cc935679b84fee
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Apr 25 15:14:34 2015 +0200

    AndroidStudio: Include dictionaries
    
    Change-Id: Iaa45df3cf4a9cf4a0fb7d48f7facedbc165f0e6d

commit 6adee1e1e3410ad2adcc2e06f7d47c3c1a877a94
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 02:52:12 2015 +0200

    Import translations from crowdin

commit b972ea2e57c17cae9f57486c7a77056b04bcd9e3
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 15:03:02 2015 +0200

    Add option to disable hide apply on boot
    
    Conflicts:
    	app/src/main/java/com/grarak/kerneladiutor/fragments/tools/RecoveryFragment.java
    
    Change-Id: Ia55addab1f349eced892269d12f299448f8de46e

commit 368f4e305672274d44c8daf2460237dae237231f
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Apr 25 15:29:13 2015 +0200

    Bump version to 0.9.2.2
    
    Change-Id: I5545ee103c82fd71f808e6505100ce7b6d64340e

commit ade351cf74b727608a618b3d670ceb8e26d38532
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Apr 25 19:00:44 2015 +0200

    AndroidStudio: Bypass lint errors
    
    Change-Id: I3c2894a3cc5f0f9d90ff318e17daf0d2af1bb5b8

commit 5c422b434724de3e9c3f86cfbd0703395ef8b2c2
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Apr 25 19:02:09 2015 +0200

    AndroidStudio: Updates
    
    Change-Id: I23cc2f4b069afc916398bb58ea156a844f5a475d

commit b25ef69c168d8a3edeb06ea2d703dc4998b551b5
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Apr 25 17:36:52 2015 +0200

    Add missing FileBrowserActivity
    
    Change-Id: I5327f5f3b8e719e53961b863785b93c8b63246a4

commit e120520aa0c6ce05523dde72913f929009f3ebd9
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sat Apr 25 18:58:30 2015 +0200

    FileBrowser: Fix FC caused by /storage/usbdisk
    
    Documentation of listFiles() : ...Returns null if this abstract pathname does not denote a directory, or if an I/O error occurs.
    
    Change-Id: I1665704a048e73cb24effe94e8fb93abc1b02191

commit 879c0d9a874442f7656c7d0b33b6742c44ad124c
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 15:45:22 2015 +0200

    Remove some unnecessary return functions

commit 76aebd33a27ccc812c192542c57ac96aba8cfd5e
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 22:36:23 2015 +0200

    Add Init.d support
    
    Conflicts:
    	app/src/main/java/com/grarak/kerneladiutor/fragments/kernel/MiscFragment.java
    	app/src/main/res/values/arrays.xml
    
    Change-Id: I50dc39ecf96bc4391c5faa8f99cdc3cdebbb0d2f

commit 356f73bac0b6d41bd6450976245ed48017617178
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 23:06:41 2015 +0200

    version 0.9.3

commit 8c499aeab33db928ba2538196bbeadb2dad1d5b7
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 23:11:05 2015 +0200

    Import translations from crowdin

commit bb9b86b0c7131a23ea6e33e29d60124d12a03ea2
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 23:44:40 2015 +0200

    Init.d: Pathreader: Some fixes
    
    Conflicts:
    	app/src/main/java/com/grarak/kerneladiutor/fragments/tools/InitdFragment.java
    
    Change-Id: Icaeae57669f549ddae60493a03c01ec00ff1178b

commit a979580a278f34ce82d5470e2f1a012b86bf650c
Author: Willi Ye <williye97@gmail.com>
Date:   Sat Apr 25 23:49:44 2015 +0200

    Import translations from crowdin

commit 1a5c995bad1c29cd877d5fd9e418f7f0a7118637
Author: Willi Ye <williye97@gmail.com>
Date:   Sun Apr 26 01:15:22 2015 +0200

    Add support for vdd voltage

commit 0ab4b44614f7deed6756734f8fa8bddff4d27c1e
Author: Willi Ye <williye97@gmail.com>
Date:   Sun Apr 26 11:17:51 2015 +0200

    Voltage: Fix vdd levels
    don't divide voltage by 1000

commit 3517c185f38cba8be1e22d466db5a6d13993b541
Author: Willi Ye <williye97@gmail.com>
Date:   Sun Apr 26 14:03:47 2015 +0200

    Some UI fixes
    move dimens to values

commit 604a77b9494cb65726cdafe970962fb0abc6c2e6
Author: Willi Ye <williye97@gmail.com>
Date:   Sun Apr 26 16:57:23 2015 +0200

    Update README.md

commit d6766c921268bcfb3d8cbcdd02db3190bd8d7d3f
Author: Willi Ye <williye97@gmail.com>
Date:   Sun Apr 26 17:13:12 2015 +0200

    Don't start animation if fragment is not attached
    
    Conflicts:
    	app/src/main/java/com/grarak/kerneladiutor/fragments/RecyclerViewFragment.java
    
    Change-Id: Ibab5ca804092f1d3f006a830625847220704e1fb

commit 8fffb2836d2bb971fcd6b9fc8372eb08929d0236
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sun Apr 26 20:09:52 2015 +0200

    AsyncTask: Execute it on a thread pool
    
    Change-Id: I5cb085505503d72d22fb6e11497d472e9aa5f347

commit 6fa9e6c6ff0e3b1090c9c914918a15169a84c380
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sun Apr 26 20:11:37 2015 +0200

    Bump version to 0.9.3
    
    Change-Id: I69e1ac6b0ec771c7a88858052e389a7ae113dc51

commit a45ecf0ee820f0cc99f6f1080c13002809072b5e
Author: Willi Ye <williye97@gmail.com>
Date:   Sun Apr 26 21:07:12 2015 +0200

    Add more wakelock controls
    
    Conflicts:
    	app/src/main/java/com/grarak/kerneladiutor/utils/Constants.java
    
    Change-Id: I1f14be6c33148a6891db8d803553b47bb956e8fa

commit 5c13c94b644b03c2b6d71bf8b749ea298eaae0b6
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Mon Apr 27 00:15:00 2015 +0200

    Misc: Fix android logging not showing up
    
    Change-Id: I5b9ce3cd5d75ff30e9df2981ff14783f162bdd45

commit b6090c6a346545d9d2c2acdf19520e352b20be97
Author: Willi Ye <williye97@gmail.com>
Date:   Mon Apr 27 13:33:38 2015 +0200

    Replace ListViews with Recyclerviews
    This contains ugly hacks
    I'm too lazy to write a good code
    
    Conflicts:
    	app/src/main/java/com/grarak/kerneladiutor/utils/Constants.java
    
    Change-Id: I0b24292d243c13bb03be47e5b70a13a2671d64fe

commit 99ec141c01e42d3bb75c6584e76bb9a68e9f7f2a
Author: Willi Ye <williye97@gmail.com>
Date:   Mon Apr 27 14:16:08 2015 +0200

    Refresh the navigation drawer

commit 0ba46554fbd23274b082acb488249036e0b31fb3
Author: Willi Ye <williye97@gmail.com>
Date:   Mon Apr 27 14:46:41 2015 +0200

    FileBrowser: Show a toast if path does not contain any files

commit 56176fde12a2594889304007be685d127ca83fb9
Author: Willi Ye <williye97@gmail.com>
Date:   Mon Apr 27 15:29:39 2015 +0200

    Remove unused things
    and some clean ups

commit 37be224b892a7f3465db0a1137e930721365d882
Author: Willi Ye <williye97@gmail.com>
Date:   Mon Apr 27 15:31:09 2015 +0200

    Import translations from crowdin

commit 6e9527e2226e55cb4329fc507cb8b1126b651489
Author: Willi Ye <williye97@gmail.com>
Date:   Mon Apr 27 15:33:04 2015 +0200

    version 0.9.3.1 beta

commit cbc09d268b46dd8cfef71fc6116d7b15872b30de
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Mon Apr 27 19:31:13 2015 +0200

    Constant: Set VERSION_NAME to 'prebuilt'
    
    BuildConfig is generated by AndroidStudio and therefore it is not available when building the app within ROM
    
    Change-Id: I8a42234af830280c7ebd3e9d9dbfde263a084b4d

commit 086c86d4925744a6f100d77e2a860ac412f3b32c
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Mon Apr 27 19:35:10 2015 +0200

    Bump version to 0.9.3.1
    
    Change-Id: I78d54982c4e7f47a445df91e0185960008e3cf57

commit c60ab83ef4555e5c8268d8124a28b3b2e313caae
Author: Willi Ye <williye97@gmail.com>
Date:   Mon Apr 27 23:36:40 2015 +0200

    Add comments and don't divide by 0

commit ff7b88e3a45ad4186f5a019cfe0fb3dc1c7737a1
Author: Willi Ye <williye97@gmail.com>
Date:   Tue Apr 28 00:03:08 2015 +0200

    version 0.9.3.1.1 beta

commit 7ffd04ad66026d4b51c0bfbee1f9bceb20c78855
Author: Willi Ye <williye97@gmail.com>
Date:   Tue Apr 28 21:10:44 2015 +0200

    Fix gamma profiles not showing up
    and add a wakelock section in misc

commit 5da0f384d74bba5e64a08b4fd1820f81891841c0
Author: Willi Ye <williye97@gmail.com>
Date:   Tue Apr 28 21:20:21 2015 +0200

    version 0.9.3.1.2 beta

commit 6dcb4e63bb8fbe115b23d3ab5a543bd429f2d002
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Tue Apr 28 22:23:53 2015 +0200

    Bump version to 0.9.3.1.2
    
    Change-Id: I2c84d4abc4f31870b9285b43b001709fe51e16e2

project packages/apps/LockClock/
commit a9d5e24675876258692cf5f019b1cfa2c00d6a16
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:14:38 2015 +0300

    Automatic translation import
    
    Change-Id: I235ca0092b8739aed0f0814fb84be0dde9e87c62

commit 3ba3c001338e369053fb9a655ff2df80929c8ea1
Author: Martin Brabham <optedoblivion@cyngn.com>
Date:   Fri Apr 24 15:36:58 2015 -0700

    Revert "cLock: Add to launcher"
    
    This reverts commit 500804d7530802f34b21d1e230b207efedc7d56b.
    
    Change-Id: I3592c903ac262a58e70e121ec242ac784775ba1f

project packages/apps/Mms/
commit c52d75c70553ec55f191e74df277acd0878422a8
Author: Matthieu Baerts <matttbe@gmail.com>
Date:   Tue Apr 15 00:20:05 2014 +0200

    Revert "Remove smiley support"
    
    This reverts commit c7c68dba4f3440f234f65eef579f9aaa82682f8c.
    
    It seems that the smiley support has been removed by a Google Dev (Tom Taylor)
    without any explanations:
        https://android.googlesource.com/platform/packages/apps/Mms/+/c7c68db
    
    This modification gets the smiley back:
     * ASCII Smileys are converted to images in all received/sent messages.
     * A new menu entry (Insert smiley) is available in the menu of a conversation
       view (ComposeMessageActivity).
    
    I also added this support in QuickMessage too (by parsing the message
    just before sending it to the TextView).
    
    PAC-Rom Change-Id: I59be9aaed9218459452274c743b71df72d0927ff
    Change-Id: Ic3f7005a2c2485405a9259f3ede7fc5ad40336e0

commit a479ce22dddb8505d6f67ee6df06b3a3196e7868
Author: Vladislav Koldobskiy <admin@nevergone.ru>
Date:   Sun Jun 8 17:32:40 2014 +0400

    Hide "Insert smiley" if emoticons are disabled
    
    There's no point in having "insert smiley" option when
    graphical emoticons are disabled.
    I still hate these emoticons.
    
    Change-Id: I2b811015910811e211c9e3e203532f19c29a0638

commit 09bb7359513cbf6b3248d9a0407a05dd11a651ff
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:14:42 2015 +0300

    Automatic translation import
    
    Change-Id: I8313d9db76cf40ad1bd585806f8a552d6b56b59f

commit 1f3ff020a1e016ecff1dae19a00316c509ffa9b2
Merge: 75dcf8c 09bb735
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:08:47 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

project packages/apps/Profiles/
commit e77bc46f9d05b9c2f0eb2b37be2227e993fd6efa
Author: Roman Birg <roman@cyngn.com>
Date:   Mon Apr 20 18:12:53 2015 -0700

    ProfilesTrustAgent: initial implementation
    
    Change-Id: I6aba123f81fd872e8ac6be532d8ec3995522daf2
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 8fa506205ec1fdeabd965d3622a825ddfe30794c
Author: Roman Birg <roman@cyngn.com>
Date:   Sun Apr 26 11:07:19 2015 -0700

    StartUpReceiver: handle case when there were no trust agents
    
    Change-Id: I2261c1720e6b69c1bbb15d2fa3b0536be855ec3a
    Signed-off-by: Roman Birg <roman@cyngn.com>

project packages/apps/Settings/
commit 6a65d1c18b08b3df078ead1cc383fda36fb3b337
Author: Raj Yengisetty <rajesh@cyngn.com>
Date:   Thu Apr 23 15:27:25 2015 -0700

    Settings: pass intent extra EXTRA_REQUIRE_PASSWORD after selecting pattern size
    
    Change-Id: I4b851e69610f16203d10e70cec6b73b563193b9b

commit 035b9a684f8d6e94b1be4c0f23f36d69afe8a9b7
Author: DvTonder <david.vantonder@gmail.com>
Date:   Wed Apr 22 11:38:21 2015 -0400

    Settings: Allow/Prevent notification light in Zen mode (2 of 2)
    
    This allows the user to prevent the notification lights from showing during Zen mode as per Android 5.0.x
    
    Change-Id: Ia3563d79f5c1fc012411496c7b8901099a78282e

commit d8fba7ac1889044b9ab4f2d3a933fffe74806576
Author: Roman Birg <roman@cyngn.com>
Date:   Mon Apr 20 16:23:02 2015 -0700

    Settings: allow more than one trust agent
    
    Change-Id: I6ae3e6c7e37ae4e203676e6c664210e2f63d8215
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit ba39107e372336574bc9ffe9c02bbaf1fb876e26
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 01:39:26 2015 -0700

    Allow launching notification manager settings externally
    
    Change-Id: Ic9acab571fc78d139d4924f9a95194423bf1d267

commit 380572d9b547a535d82a82b9c9d60a490633ce1a
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 01:44:10 2015 -0700

    Revert: Option to use volume keys to control media volume anytime [2/2]
    
    The volume keys control the Media volume rather than the Ringer
    hence removing the issue of accidentaly changing the Ringer volume.
    
    Credits: Pawitp
    
    Change-Id: Ic0a1c04ae41eac65e9535d6de5f11c0456730315
    
    Conflicts:
    	res/values/cr_strings.xml
    
    (cherry picked from commit 82e813263298ab084a1f428489b3ea2fcd5a23b9)
    Revert "Option to use volume keys to control media volume anytime [2/2]"
    
    This reverts commit 9493e927849b0c4e548953f9409f2548aaf196bb.
    
    Conflicts:
    
    	res/values/cr_strings.xml

commit a821e0bc944871bd2b9070403bd349a0a582005e
Author: Pawit Pornkitprasan <p.pawit@gmail.com>
Date:   Sun Apr 21 22:52:33 2013 +0700

    Option to use volume keys to control media volume anytime (1/2)
    
    Some users don't adjust ringtone volume often (e.g. only use toggle to
    switch between silent and non-silent) mode. Having an option to
    use the volume keys to control media volume anytime allows media
    volume to be controllled/muted before entering a game or other apps
    with sound in an undesirable location.
    
    Change-Id: I6dbd25d1a14bcf5b1bf0b0468b96f4b4f8efdb14
    
    Conflicts:
    
    	src/com/android/settings/ButtonSettings.java

commit 37ac18ad584f65b7e88be040133027ada7b4320d
Author: Roman Birg <roman@cyngn.com>
Date:   Thu Feb 19 14:05:03 2015 -0800

    Settings: use correct default value for backlight brightness
    
    When the user has enabled the nav bar through the setupwizard and
    returns back to the buttons settings and toggles the nav bar off, the
    backlight brightness would not be restored because there was no previous
    value to read from, so use the default framework value if none exists.
    
    Change-Id: If4ce90bcde3c9a59f26e49be2c585df844ead6bd
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 29372596a72bb5b7850ef27c35fe523e93ddb24b
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:14:50 2015 +0300

    Automatic translation import
    
    Change-Id: I6fb39fdee4fa4a9bfda42d180f6cf5180bb84c1d

commit 6902cf383902e4d1d0dd738a07c324c8b6b6bb98
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 15:39:10 2015 -0700

    [Squash] Revert Slim stuffs
    
    Revert: Settings: Slim Actions to Shortcuts
    
    Change-Id: I8c9a524f3628c47e882347225372ff065b4f2b94
    
    Conflicts:
    	res/values/cr_arrays.xml
    
    Conflicts:
    	res/values/cmr_arrays.xml
    	res/values/cmr_strings.xml
    
    Conflicts:
    	res/values/cmr_arrays.xml
    	res/values/cmr_strings.xml (reverted from commit 8795806a9331b2ecea82f35eda92ed88886fe06e)
    Revert: Settings: SlimAction as QuickTile (2/2)
    
    Configure which Slim actions you want to use as tile and then add the 'SlimAction' tile.
    Single press will switch between Slim actions and long press will execute the Slim action. If the tile has only one Slim action, single press will execute the action.
    
    Change-Id: I6a01ca065801a2ceabf1b0c21dc9d9c0a0289af2
    
    Conflicts:
    	res/xml/notification_drawer_settings.xml
    
    Conflicts:
    	res/values/cmr_arrays.xml
    	res/xml/notification_drawer_settings.xml
    
    Conflicts:
    	res/xml/notification_drawer_settings.xml
    	src/com/android/settings/cyanogenmod/qs/QSTileHolder.java (reverted from commit a3aef7066f2b3d8e7bf03e3d4d658093ada3c7f4)
    Revert:  [2/2] Settings: Configurable overflow menu button
    
    Forward port from SlimBean. It was part of the hardware key custom rebinding.
    
    (cherry picked from commit 10e658f258a07f8aa2961c2eca266f08b7ff47e4)
    
    Conflicts:
    	res/values/cmr_strings.xml
    	src/com/android/settings/ButtonSettings.java (reverted from commit b96ffd5f6ac36930c189d64c43e8a6bb9a48d81d)
    
    Change-Id: I5b1edf45c30beb1b23f115235b72a68a52af0cfa
    Revert "Fix NPE on overflow due to removal of HW Keys category"
    
    This reverts commit 558e4704b56a527f3da2b6fb6ba7a6db1d24ba49.
    
    Change-Id: I24d10e29f739d0a9cdf80cbbddee550877d69d55

commit 9e0d9387a10bb92050804642dfe3d912f07d363d
Author: Dragon <dragon7780@hotmail.nl>
Date:   Sat Apr 25 03:02:25 2015 -0700

    Settings: SlimPie (2/2)
    Implement SlimPie for lp5.0 ported from kitkat.
    
    PS1: Implement SlimPie based on Fusion Commits
    
    WIP
    Still need to bring back a few more SlimPie features.
    
    Change-Id: I4c60d3e2bea1bc30969d74d7373848d33820143c
    Signed-off-by: Dragon <dragon7780@hotmail.nl>

commit d6944b14e1230f8cd7bead35180f00cb9ebdcaaf
Author: Lars Greiss <kufikugel@googlemail.com>
Date:   Sat Apr 25 05:16:58 2015 +0300

    Add link to Privacy Guard from app info screen
    
    Based on https://github.com/SlimRoms/packages_apps_Settings/commit/46bb1442aa96aad6890e3ce7b6f3c0466ababf25
    
    JIRA: CYAN-3826
    Change-Id: I9591ee7b0ffcce7f2257f988bc2aa5dcf39be4ff

commit dca2179324d263c622a8bbc69c4aad6e2293cc85
Author: ZION959 <ziontran@gmail.com>
Date:   Sun Apr 26 15:54:04 2015 -0700

    Revert: [1/2] Kernel Auditor Tweaker
    
    Change-Id: I571b7f25b20f8edac31434317e6b76ebb3e6d6df (reverted from commit 67a0de7973ae81fb136de66e332b0bdf1feedd8e)

commit 40a28d44a505b6cce10231a37abf877dd9e1174c
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Sun Apr 26 16:07:26 2015 -0700

    Settings: Add shortcut to KernelAdiutor
    
    Change-Id: Ibe1ece98d542d81a990472180f6ab3e355a31e4b
    
    Conflicts:
    	AndroidManifest.xml
    	res/values/slim_strings.xml
    	res/xml/dashboard_categories.xml

commit 4442c7b600f7e03457cdd3a7670c6e03b36c2328
Author: Janson Kang <temasek71@gmail.com>
Date:   Sun Apr 26 08:47:22 2015 +0800

    Move "Allow lights" in zen mode to "Allow alarms" category

commit dfc604a33c6ece3679307c27eb361cbc5e73dc17
Author: Jubakuba <Jubakuba@gmail.com>
Date:   Sun Apr 26 16:25:34 2015 -0700

    Settings: Slim Actions to Shortcuts

commit 676ee7800d73f9490111e8114457c84c1ced2b69
Author: tristan202 <tristan202@gmail.com>
Date:   Sun Apr 26 16:42:49 2015 -0700

    Settings: enable reset option to status bar clock color
    
    Reference
    https://github.com/temasek/android_packages_apps_Settings/commit/fbd59b5a38dfe4a12a97eeeb1d9055a6301399c7
    
    Modified for use in cm-12.1
    
    Conflicts:
    	src/com/android/settings/cyanogenmod/StatusBarSettings.java

commit e5949a5fc917691fa0e044de59594e7e6a0a9661
Author: ZION959 <ziontran@gmail.com>
Date:   Sun Apr 26 21:34:18 2015 -0700

    status bar house keeping

commit 644d2963134505c25566476ae953f67097aec7cd
Author: longping.zou <longping.zou@ck-telecom.com>
Date:   Wed Apr 22 20:30:34 2015 -0700

    Settings: Update sync widget state
    
    1. Go to Settings ->Accounts ->Click Menu ->Toggle Auto-sync data
    2. Go to Launcher and check the power control widget.
       The power control Widget fails to update
    
    Change-Id: I22d92be63c9ac9ef168b4193ae82e007d4a7ac1c
    (cherry picked from commit 197eedf8960835c754f2c7a4a344f9d4360bf709)
    
    Patchset: 1
    http://review.cyanogenmod.org/#/c/96337/

commit 0bcd401d1821e746328a824c1f6ceddc270ffbbe
Author: fusionjack <dogfight60-fusionjack@yahoo.de>
Date:   Mon Apr 27 02:26:56 2015 -0700

    AdvancedSettings: Build Changelog
    
    Change-Id: I707e1d79f7580a68e819b8efdcea4a1ab47839bf
    
    Conflicts:
    	res/values/slim_strings.xml
    	res/xml/slim_advanced_settings.xml

commit 90d99c4a45809e6476869c7bb4f84c5d248f8794
Author: ZION959 <ziontran@gmail.com>
Date:   Mon Apr 27 18:25:45 2015 -0700

    derp

commit c1618399e939854adb45f2653d7444c5f8eb141f
Author: Roman Birg <roman@cyngn.com>
Date:   Fri Aug 15 11:35:54 2014 -0700

    Settings: use ActivityManager method for requesting bug report
    
    This let's ActivityManagerService handle all the logic for requesting
    bug reports.
    
    Change-Id: I44e6a9295a0625bcdc0f3a22daf097bdccf0d3c4
    Signed-off-by: Roman Birg <roman@cyngn.com>
    (cherry picked from commit 3d56d11794d8a5c3637a347986c9d2908e096d19)

commit 95417ba804a67683ab0137114906b14a63d0bdfe
Author: Janson Kang <temasek71@gmail.com>
Date:   Tue Apr 28 08:01:14 2015 +0800

    Add lastapp/killapp/screenshot for PIE action selections

commit 8416d17a3b14960b311b59d2ad79b3db2ef61863
Author: ZION959 <ziontran@gmail.com>
Date:   Mon Apr 27 21:48:43 2015 -0700

    remove statusbar weather in lockscreen setings

commit 0f3e87bfefb6c73e9284028280659800f1a5a955
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Tue Apr 28 01:49:05 2015 -0700

    Saberize > update to be inline with SaberMod
    
    Change-Id: Ic69016fb27fded392215f4f20c2fe6f24f065645
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Added SaberMod Android banner in About Phone
    
    Change-Id: Id23a1ac74b4a5eac0d2f57479780eb2d0e97de68
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	res/drawable-hdpi/smbanner.png
    	res/layout/smbanner_row.xml
    	res/xml/device_info_settings.xml
    	src/com/android/settings/DeviceInfoSettings.java

commit 50ce5f2eaf29632bb809a511725c3be1419cc776
Author: Lars Greiss <kufikugel@googlemail.com>
Date:   Tue Apr 28 03:17:31 2015 -0700

    Settings: TRDS 5.0 (4/4)
    
    patchset: add holodark resources
    
    patchset: fix up switch preference
    
    patchset: add to slim actions
    
    patchset: some tweaks and fixes
    
    patchset: Action instead of SlimActions
    
    patchset: fix icon
    
    patchset: remove holodark resources
    
    patchset: add darktheme resources
    
    patchset: light sensor is experimental
    
    patchset: themeenabler uses onpreferenceclicklistener instead
            of onpreferencechangelistener
    
    patchset: add reset dialog (to reset to default theme)
    Change-Id: I5b857c542d92b9fd253b3556f14c790226594c4f
    
    Conflicts:
    	res/values/cmr_arrays.xml
    	res/values/cmr_strings.xml
    	res/xml/dashboard_categories.xml

commit 56efa7ed4cb15e06bc107beed3d15e8b85c8616b
Author: Lars Greiss <kufikugel@googlemail.com>
Date:   Mon Feb 10 23:24:51 2014 +0100

    Settings: SlimPie give user ability to reduce trigger heights if IME keyboard shows (2/2)
    
    Add a user option to reduce left and right trigger of SlimPie if keyboard shows up
    (especially usefull for swipe keyboard which most keyboards are nowadays). Enabled
    by default user can disable it in settings
    
    PS:
    - fix category string
    
    Change-Id: Ia5ae621a5e63b2efd10180cfbe1876b14a63c866

commit 7487e9474d3792da242d32c9be457f2447adeb5b
Author: Lokesh Chamane <lokesh.c703@gmail.com>
Date:   Tue Apr 28 13:47:21 2015 -0700

    SlimPIE: Configurable sensitivity [2/2]
    
    Change-Id: I7afc315bbf922f7f5ff3ba93cca38bfcd359f0ab
    Signed-off-by: Lokesh Chamane <lokesh.c703@gmail.com>
    
    Conflicts:
    	res/values/cr_strings.xml

commit bdcd1b031465a9b9b14eb531d48b47f22187574f
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 03:28:08 2015 -0700

    Revert Settings: use correct default value for backlight brightness

commit 07efc1e7cb10b6909a1569f8efa7b018a79a34ed
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 14:08:14 2015 -0700

    add SeekBarPreferenceCHOS.java

commit 99e9d858ba635c65a3c71e7b44a107340cbff12e
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 14:18:48 2015 -0700

    add icon for new changelog option

commit 6ffd0ef2da05a3fef76f87e1f7308a9be580142e
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 14:25:54 2015 -0700

    reoganized slim trds

commit 87e1c5002176bbb6c6148a71c8ba06d39ccfe682
Author: Janson Kang <temasek71@gmail.com>
Date:   Wed Apr 29 21:55:12 2015 -0700

    Fix breathing sms/misscall/voicemail + add mobile check
    
    Conflicts:
    	res/values/cmr_strings.xml
    	res/xml/status_bar_settings.xml

commit 1d99a053e21610a4f900481ece62016bb43955c2
Author: Utkarsh Gupta <utkarsh.eminem@gmail.com>
Date:   Wed Apr 1 00:00:00 2015 +0000

    [2/2] Battery light: 100% charged level

commit 3779f65aadefd97a8288859a27147304ba679774
Author: Utkarsh Gupta <utkarsh.eminem@gmail.com>
Date:   Wed Apr 1 00:00:00 2015 +0000

    Allow restricted profiles on phones

commit 7354ab876592d840eba37c3a3d355bc59295d3ae
Author: Utkarsh Gupta <utkarsh.eminem@gmail.com>
Date:   Wed Apr 1 00:00:00 2015 +0000

    Re-enable CPU governor & min/max freq settings

commit d23c677e4a50d8dfb0833c0c6417defe2d6f1e43
Author: Janson Kang <temasek71@gmail.com>
Date:   Wed Apr 29 15:03:27 2015 +0800

    Update PIE Control

commit f41f19f5bb79886ef6e1d8e0aefec5de9caa16a1
Author: Altaf-Mahdi <altaf.mahdi@gmail.com>
Date:   Sun Mar 1 19:15:34 2015 +0000

    Display settings: show enabled/disabled summary for ambient display
    Change-Id: I97aee7aafd69f3e60d2c518aa514a7cd1dff9ecf
    
    Conflicts:
    	res/values/custom_strings.xml

commit 3a9299f4bc2a6279a06e247bceb7475ee3d6f0bc
Author: Altaf-Mahdi <altaf.mahdi@gmail.com>
Date:   Wed Apr 29 21:37:19 2015 -0700

    Display settings: remove ambient display screen when advanced mode is disabled
    
    now when advanced mode is disabled ambient display will be a simple switch preference
    
    Change-Id: Ia50897590b56a7d295255828da3d62e9535c0c60
    
    Conflicts:
    
    	res/xml/display.xml
    	src/com/android/settings/DisplaySettings.java
    
    Conflicts:
    	res/xml/display.xml

commit 02d9731e7d55eec9b6b202956931b02564f4a924
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Thu Apr 30 10:30:58 2015 -0700

    Optimize Settings png's
    
    Change-Id: I70b309c97e924b88267bca6b74e0ccbc3f172637
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	res/drawable-hdpi/ic_power_system.png
    	res/drawable-hdpi/ic_settings_cell_standby.png
    	res/drawable-hdpi/ic_settings_phone_idle.png
    	res/drawable-hdpi/ic_settings_voice_calls.png
    	res/drawable-hdpi/ic_sync_anim_holo.png
    	res/drawable-hdpi/ic_sync_error_holo.png
    	res/drawable-hdpi/ic_sync_grey_holo.png
    	res/drawable-hdpi/ic_wps_dark.png
    	res/drawable-hdpi/ic_wps_light.png
    	res/drawable-hdpi/nfc_payment_empty_state.png
    	res/drawable-mdpi/ic_bt_network_pan.png
    	res/drawable-mdpi/ic_power_system.png
    	res/drawable-mdpi/ic_settings_cell_standby.png
    	res/drawable-mdpi/ic_settings_phone_idle.png
    	res/drawable-mdpi/ic_settings_voice_calls.png
    	res/drawable-mdpi/ic_sync_anim_holo.png
    	res/drawable-mdpi/ic_sync_error_holo.png
    	res/drawable-mdpi/ic_sync_grey_holo.png
    	res/drawable-mdpi/ic_wps_dark.png
    	res/drawable-mdpi/ic_wps_light.png
    	res/drawable-mdpi/nfc_payment_empty_state.png
    	res/drawable-xhdpi/ic_bt_network_pan.png
    	res/drawable-xhdpi/ic_item_delete.png
    	res/drawable-xhdpi/ic_power_system.png
    	res/drawable-xhdpi/ic_settings_cell_standby.png
    	res/drawable-xhdpi/ic_settings_phone_idle.png
    	res/drawable-xhdpi/ic_settings_voice_calls.png
    	res/drawable-xhdpi/ic_sync_anim_holo.png
    	res/drawable-xhdpi/ic_sync_error_holo.png
    	res/drawable-xhdpi/ic_sync_grey_holo.png
    	res/drawable-xhdpi/ic_tab_selected_download.png
    	res/drawable-xhdpi/ic_tab_selected_running.png
    	res/drawable-xhdpi/ic_wps_dark.png
    	res/drawable-xhdpi/ic_wps_light.png
    	res/drawable-xhdpi/nfc_payment_empty_state.png
    	res/drawable-xxhdpi/ic_bt_network_pan.png
    	res/drawable-xxhdpi/ic_item_delete.png
    	res/drawable-xxhdpi/ic_power_system.png
    	res/drawable-xxhdpi/ic_settings_cell_standby.png
    	res/drawable-xxhdpi/ic_settings_phone_idle.png
    	res/drawable-xxhdpi/ic_settings_voice_calls.png
    	res/drawable-xxhdpi/ic_sync_anim_holo.png
    	res/drawable-xxhdpi/ic_sync_error_holo.png
    	res/drawable-xxhdpi/ic_sync_grey_holo.png
    	res/drawable-xxhdpi/ic_tab_selected_download.png
    	res/drawable-xxhdpi/ic_tab_selected_running.png
    	res/drawable-xxhdpi/ic_wps_dark.png
    	res/drawable-xxhdpi/ic_wps_light.png
    	res/drawable-xxhdpi/nfc_payment_empty_state.png
    	res/drawable-xxxhdpi/ic_bt_network_pan.png
    	res/drawable-xxxhdpi/ic_power_system.png
    	res/drawable-xxxhdpi/ic_settings_phone_idle.png
    	res/drawable-xxxhdpi/ic_sync_anim_holo.png
    	res/drawable-xxxhdpi/ic_sync_error_holo.png
    	res/drawable-xxxhdpi/ic_sync_grey_holo.png
    	res/drawable-xxxhdpi/ic_tab_selected_download.png
    	res/drawable-xxxhdpi/ic_tab_selected_running.png
    	res/drawable-xxxhdpi/nfc_payment_empty_state.png

commit 0b39c4336d5199dda88f460f1f026bb171201498
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Thu Apr 30 10:32:34 2015 -0700

    Remove extra kernel gcc version info (1/2)
    
    No longer needed with 9590f426e7986e64d68ae80b4ac5c6409f4c88b5
    
    Change-Id: Idd694e9616fa9875aa3911e58ec8a4e526423c0b
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	res/values-eu-rES/cm_plurals.xml

commit 9e0dcced98f3deaff0fb5d23a2895246703889d6
Author: Shaun Eaton <shaunsibu@gmail.com>
Date:   Mon Apr 27 22:53:25 2015 -0600

    Lets use Dark Material colors
    - TRDS will switch to use these colors.
    - We have permission from @nicholaschum to use these colors for our TRDS.
    - Add more white icons and remove the ones that we do not use.
    
    Change-Id: Ia3012e3f4ffddf8ff560822fca27fad62118c561

commit ee24d426a5d5cf2793f6ed95f9e40d72c1fa16df
Author: ZION959 <ziontran@gmail.com>
Date:   Thu Apr 30 11:46:22 2015 -0700

    remove leftover breathing sms/misscall/voicemail

commit e01b6b2f77c9b2e38b0ec5afcf15d9874b1b4562
Author: Altaf-Mahdi <altaf.mahdi@gmail.com>
Date:   Wed Apr 15 19:03:00 2015 +0100

    Settings: enable/disable doze through Profiles (2/2)
    
    * moved isDozeAvailable boolean to Utils so we can check for it in profiles
    
    Change-Id: I5a768098b4ed00b28931bee58a58efa8280262a1
    
    Conflicts:
    
    	src/com/android/settings/DisplaySettings.java
    	src/com/android/settings/Utils.java

commit 25b55e41b24bd73d1619813eec9bd71390b97a3d
Author: ZION959 <ziontran@gmail.com>
Date:   Thu Apr 30 14:51:21 2015 -0700

    Revert: Remove extra kernel gcc version info (1/2)
    
    No longer needed with 9590f426e7986e64d68ae80b4ac5c6409f4c88b5
    
    Change-Id: Idd694e9616fa9875aa3911e58ec8a4e526423c0b
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	res/values-eu-rES/cm_plurals.xml (reverted from commit 0b39c4336d5199dda88f460f1f026bb171201498)

commit f6fafbfd0b640d9fc7d58d97c194fd214764329a
Author: Roman Birg <roman@cyngn.com>
Date:   Tue Apr 28 14:02:21 2015 -0700

    CryptKeeper: pattern unlock displays incorrect pw when correct
    
    fakeUnlockAttempt() gets called when the user inputs any pattern length
    < 4 which queues up the 'incorrect error' message. The message needs to
    be cleared before trying to actually check the password so it never goes
    through in case the password was correct.
    
    Change-Id: If78db332d3d696ba443d0be911fb5db504cb14cd
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 91f09fd9c2590455f886c411c7db83f9a97c8d26
Author: tobitege <tobiasteschner@googlemail.com>
Date:   Wed Apr 29 21:17:05 2015 +0200

    Fix NPE in slim shortcut if no icon was found
    
    Change-Id: If7adfdb82a8d014ab44ab74670b7a0e1655ecb9d

project packages/apps/SlimLauncher/
commit 545bd8acc5ebeadcb14f7e3fda51b875ef8fa274
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Tue Oct 14 16:12:12 2014 -0700

    Moving the focus indicator instantly to the target position, instead
    of begining the next animation from the middle.
    
    Bug: 17958897
    Change-Id: Ie5a39b80ff9788edf368e0f4e23c07c2ed5b3d2c

commit d357d5884c55ad8bdcf4a5c9fde9fae3c119778d
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Tue Oct 14 16:42:54 2014 -0700

    Adding NPE check in InstallShortcutReceiver
    
    > Removing some unused methods
    
    Bug: 17971165
    Change-Id: I1bc5c764fd65b44c950a58371b60d2b53c221995
    
    Conflicts:
    	src/com/slim/slimlauncher/InstallShortcutReceiver.java

commit c0ed928b5dba9a3428b670a5e1e83c953c6022ff
Author: Geoff Mendal <mendal@google.com>
Date:   Wed Oct 15 10:46:05 2014 -0700

    Import translations. DO NOT MERGE
    
    Change-Id: Ied5954dcd88f900ae2f9e21b1ec0cdbe01cad06b
    Auto-generated-cl: translation import
    
    Conflicts:
    	res/values-ms-rMY/strings.xml

commit db34f57223d235b9f6b2766939bd6f5029a93f9f
Author: Adam Cohen <adamcohen@google.com>
Date:   Tue Oct 7 18:14:53 2014 -0700

    Use LauncherCallbacks model instead of method overrides
    
    -> When extending the Launcher Activity, instead of overriding
       public and protected methods, create a proper interface
    -> This helps define the interface when extending Launcher
       more formally and more clearly
    
    Change-Id: Ib38e8a376b2242d4078bf6856bb145f5b5f0da80
    
    Conflicts:
    	src/com/slim/slimlauncher/Launcher.java

commit 4de7ca7d870c52a77e7245d5732085d7480e98cb
Author: Helena Josol <helenajosol@google.com>
Date:   Thu Oct 9 17:04:09 2014 +0100

    Add more Launcher files to delete on Clear Launcher Data
    
    Bug: 12753154
    Change-Id: I00679bdc6eff70a1398122aaa955c08eabd556b1
    
    Conflicts:
    	src/com/android/launcher3/LauncherFiles.java
    	src/com/slim/slimlauncher/Launcher.java
    	src/com/slim/slimlauncher/LauncherAppState.java

commit 41b08e1d8428caf3f30088e2c60b93694d1ea91b
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Wed Oct 8 10:47:28 2014 -0700

    Showing widgets in a disabled state, when running in safe mode
    
    Bug: 15172107
    
    Change-Id: I7209836ca4ffacde7b7b232e230e9b9f1a0e54bb
    
    Conflicts:
    	src/com/slim/slimlauncher/Launcher.java

commit 1fad5f6bbb79cf95bab3d207c2f08ab31112e043
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 16 12:08:41 2014 -0700

    Not opening all apps again when AppInfo or Uninstall is selected
    
    Bug: 17460202
    Change-Id: Id67a9637324abceb5b446fff5999db2a0910401b
    
    Conflicts:
    	src/com/slim/slimlauncher/DeleteDropTarget.java

commit 3beca13868f89e47b13d43bf655dd9123319993a
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 16 12:18:37 2014 -0700

    Deleting workspace items from db which have an invalid placement
    
    Change-Id: I1d616e8cd533acd6ecd334d85e6468163f31f6a4
    
    Conflicts:
    	src/com/slim/slimlauncher/LauncherModel.java

commit 91682ebd5422f68c7767cd163e93ddbb85f11a29
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 16 14:07:29 2014 -0700

    Fixing some IconCache methods not  thread safe
    
    Bug: 17981568
    Change-Id: I0d49604c2e38bc9017cba527d87e24e8b086f1da
    
    Conflicts:
    	src/com/slim/slimlauncher/IconCache.java

commit c0c5b1c6323f7c16437dcf244ab334c1802b90d2
Author: Adam Cohen <adamcohen@google.com>
Date:   Thu Oct 16 09:49:52 2014 -0700

    Adding ability to list folder items in separate file
    
    -> remove all apps default layouts
    
    Bug 17569015
    
    Change-Id: I39b899b61d5b1cff2d7801d281dacfc804c403c5
    Conflicts:
    	res/xml/default_workspace_4x4_no_all_apps.xml
    	res/xml/default_workspace_5x5_no_all_apps.xml
    	res/xml/default_workspace_5x6_no_all_apps.xml

commit 3ad1b131e5eee559d8762db54659e107f5d31dab
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 16 16:03:21 2014 -0700

    Removing all traces of Market button and TabIndicator
    
    Change-Id: I9dc10d990321697723560986834ebeef3e0f1c0d
    Conflicts:
    	res/layout/tab_widget_indicator.xml

commit b2075788be152468eff651b86808a10dcb1bf8b2
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Wed Oct 1 15:33:41 2014 -0700

    Refactoring layout parsing code
    
    Change-Id: Iee5b2280cb1e841bcfe91fdcf523de6fa7f7f3b8
    
    Conflicts:
    	src/com/slim/slimlauncher/AutoInstallsLayout.java
    	src/com/slim/slimlauncher/LauncherProvider.java

commit 01fdc0d28686b6049b19e4da3cf988710aecc67c
Author: Nick Kralevich <nnk@google.com>
Date:   Sat Oct 18 06:57:06 2014 -0700

    fix build
    
    Bug: 18040469
    Change-Id: I24db4d3f4b7ee10ecf5a2c65035ce112271539fb

commit 47cb8e237f55e6332f081b49d857735ea3cd0ffb
Author: Nick Kralevich <nnk@google.com>
Date:   Sat Oct 18 08:14:09 2014 -0700

    fix build
    
    Bug: 18040469
    Change-Id: I2938c7b950470eeacfb20391f109ae44d95060c7

commit a956d490a619f0a212e153882e40dd0a2fd20c35
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Tue Oct 21 10:04:54 2014 -0700

    Removing AccessibleTabView and some other dead code.
    
    Change-Id: Ia122a6277f924e6077dbf15a4dc40b5042aa987d
    
    Conflicts:
    	src/com/slim/slimlauncher/AccessibleTabView.java

commit 86c9afd1fdcf08714228ea04d9a617316d91c251
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 23 11:09:18 2014 -0700

    Removing landscape string overrides
    
    Change-Id: Idbfc600dfb32b195726f1b035d18be92c26883fd

commit 37ce7fe8fdb54f3bb336e6daf0ef901596c49edb
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 23 11:38:15 2014 -0700

    Some resource fixes for drop target
    
    > Making it singleline with ellipsis everywhere
    > Decreasing the text size on smaller devices
    > Decreasing char limit for various labels
    
    Bug: 17563793
    Bug: 17938450
    Change-Id: I8ad1a156de0601d07419b2cc6418389bc2e24a4e
    
    Conflicts:
    	res/layout/drop_target_bar.xml
    	res/layout/search_drop_target_bar.xml
    	res/values/styles.xml

commit 5b21fc82539bc3aa143bd1fe2dc5d76e6505df22
Author: Adam Cohen <adamcohen@google.com>
Date:   Thu Oct 23 17:28:30 2014 -0700

    Allow LauncherOverlay to access and manage insets
    
    Change-Id: Ib9faf37eb22ad2a0b18c076978ec9f2fd8864c0c
    
    Conflicts:
    	res/layout-land/launcher.xml
    	res/layout-port/launcher.xml
    	res/layout-sw720dp/launcher.xml
    	res/layout/launcher_overlay_example.xml
    	res/layout/tab_widget_indicator.xml
    	src/com/android/launcher3/LauncherCallbacks.java
    	src/com/android/launcher3/LauncherExtension.java
    	src/com/slim/slimlauncher/DragLayer.java
    	src/com/slim/slimlauncher/Launcher.java

commit 75df5446b9eb8bc53fb6318633371668af93e293
Author: Adam Cohen <adamcohen@google.com>
Date:   Fri Oct 24 12:20:20 2014 -0700

    Was seeing some duplicated icons in the migration flow
    
    -> The only delta between the two icons was slightly different flags
    -> No need to consider flags for the purposes of duplication
    
    Change-Id: I161f6ad6023d829e5ebbb15f1a9fbc9306795d80

commit b9ebeed5fd5fcdb8d15677d8e6da8f0f2ddb75f4
Author: Adam Cohen <adamcohen@google.com>
Date:   Fri Oct 24 16:45:59 2014 -0700

    Add InsettableFrameLayout layout params to easily ignore insets
    
    Change-Id: I117fc34627e24ea5f909c3c87e9c2dbca46babb6
    
    Conflicts:
    	res/values/attrs.xml
    	res/values/styles.xml

commit 6f208c2898f0b071ddb5638dd97dbbedd15524bd
Author: Adam Cohen <adamcohen@google.com>
Date:   Fri Oct 24 17:40:34 2014 -0700

    Fix edge case where LauncherOverlay scroll woudln't be reset
    
    -> If the Workspace has a single page and the user goes from overscrolling
       in one direction, and then the other, the LauncherOverlay scroll wouldn't
       be set to 0 until the scrolling settled
    
    Change-Id: I29ee9abdfa023ae3599d1590cdaebf457e2220fa
    
    Conflicts:
    	src/com/slim/slimlauncher/Workspace.java

commit 1fb9608a459fcc5a9adcc835cbbf0b9d0624fbb2
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 23 14:21:02 2014 -0700

    Loading internal default layout if partner layout fails to load
    
    Bug: 18033885
    Change-Id: I8399d0107cc3570c0e03d833601abf2cd194b3d3

commit 1c90fb3ecdb4a956eced0fe06cc520f3e432d66a
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 16 09:24:19 2014 -0700

    Updating backup restore logic
    
    > Adding DeviceProfile information in the backup
    > Removing SharedPreference backup
    > Adding helper methods to abort backup in the middle
    > Comparing keys against the backup journal during restore
    to avoid restoring corrupt/lost entries
    > Old backups are still compatible, but lost keys verification
    will be ignored in that case.
    
    Bug: 17937935
    Bug: 17951775
    Bug: 17260941
    Change-Id: Iad48646cfdd69abaff5c163b2055f3b8a9b39b19
    
    Conflicts:
    	src/com/android/launcher3/LauncherBackupAgentHelper.java
    	src/com/android/launcher3/LauncherBackupHelper.java
    	src/com/slim/slimlauncher/Launcher.java
    	src/com/slim/slimlauncher/LauncherAppState.java

commit 29f30089c321a9c7eb1aee27709cb53270d1abd0
Author: Adam Cohen <adamcohen@google.com>
Date:   Tue Oct 28 16:16:02 2014 -0700

    Make sure DragLayer layout params are of the correct type
    
    bug 18141419
    
    Change-Id: I50695a62cf9e1f25c054ac2c7197cd056d54cfae

commit 42fe4781b9810e87b4dd43f99ac64069b9923267
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Tue Oct 28 16:30:20 2014 -0700

    Fixing insets of launcher clings
    
    Change-Id: Idbf46680f96086c93d667c26dc9ed214eeaf835e
    
    Conflicts:
    	res/layout-land/longpress_cling.xml
    	res/layout-port/longpress_cling.xml
    	res/layout-sw600dp-port/longpress_cling.xml

commit 1904bc16b849be4661804b70feffc3fbce2a50a8
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 30 10:16:49 2014 -0700

    Moving methods which update internal sets on a separate thread
    
    Bug: 18152117
    Change-Id: I5fccd203b5fe65e79dcc5aead6cb1cb6c3b622fe

commit 6e4de03a69b9ec251a8cf3b07468290fd68a0118
Author: Adam Cohen <adamcohen@google.com>
Date:   Fri Oct 31 11:48:25 2014 -0700

    Adding a couple memory optimizations to Launcher
    
    -> Always dispose of widget page views when leaving the activity.
       These pages hold onto many bitmaps.
    -> Clear database cache when leaving the activity.
    
    Bug: 17967108
    Change-Id: I10ebaaed14e7cd86f09a9afcabd73043705f21b8
    
    Conflicts:
    	src/com/slim/slimlauncher/AppsCustomizePagedView.java

commit 28a3cd9ac05bd2073a3844ad6636752a1e31504a
Author: Adam Cohen <adamcohen@google.com>
Date:   Fri Oct 31 16:15:36 2014 -0700

    Overlay shouldn't show up above Intro screen
    
    bug: 18173340
    Change-Id: Icf738a55398023ab6bad5cced05b25e053dec0a2

commit 3719f1b0ccb30e0ee08fcc325f23bddf6cc3a277
Author: Adam Cohen <adamcohen@google.com>
Date:   Fri Oct 31 16:58:00 2014 -0700

    Fix folder hint text color. Likely a regression from upgrading the Activity theme
    
    Bug: 18204650
    Change-Id: I5e23df5f4f8f1f8ca7a22c8a62797e77c9a4a9e1

commit e68d8b43ed6ccc4706a5c144c24e0443144421ef
Author: Adam Cohen <adamcohen@google.com>
Date:   Mon Nov 3 16:13:45 2014 -0800

    Updating page indicator assets
    
    Bug: 17318376
    Change-Id: I4e73bf4892575bbb31f28d2cf1a4e476f8895dfa

commit a6054f4f8508ff17d75e59b61f222fd3ec426d40
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Wed Nov 5 10:34:43 2014 -0800

    Removing InstallWidgetReceiver related obsolete code.
    
    Change-Id: I61700b363f8af6434e750bcb5323e0ad4e5bf011
    
    Conflicts:
    	src/com/slim/slimlauncher/InstallWidgetReceiver.java

commit 2113224eb70d838b90eaf0c59db5542fc8484b0a
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Mon Nov 10 16:01:44 2014 -0800

    Proguard changing methods required for click feedback aniamtion
    
    Bug: 18323452
    Change-Id: Iac6d75a3c46c3a4c2a74af43bd1fca738235c2d5

commit 1bd65c5454b6caddccf7554fa14cd20bde9baac8
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Tue Nov 11 12:23:59 2014 -0800

    Removing some duplicate methods
    
    Change-Id: I8a1295ab74890984e8d8508aaa18fd79ac2a032d
    
    Conflicts:
    	src/com/slim/slimlauncher/LauncherAppState.java

commit 2474fd9491fb93da30ea1e69bd1acf4cbe123e10
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Mon Nov 10 18:05:31 2014 -0800

    Adding shortcuts corresponding to ManagedUsers automatically.
    
    Bug: 16188104
    Change-Id: Ic07578dd187263f59f3c431cbb78dea90d0c24f4
    
    Conflicts:
    	src/com/slim/slimlauncher/InstallShortcutReceiver.java
    	src/com/slim/slimlauncher/LauncherModel.java

commit dd13aac26cba839f1f8aeada074a104bb1d6dcf2
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Fri Nov 14 10:14:18 2014 -0800

    Fixing NullPointer Exception when user is deleted.
    
    Bug: 18388507
    Change-Id: I4176ea37a019c2a862e6b2875cc6b03ec9118571

commit 3f21e64f9926c6e2103cbeb42d6cc9b6a281abb6
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Fri Nov 14 11:59:57 2014 -0800

    Adding a few null checks.
      1) During migration, if launcher2 has deleted user data,
    migration oes not happen
      2) If Launcher3 does not has bind widget permission,
    QSB would be null.
    
    Bug: 18388507
    Change-Id: Ief81f6f77ce154e7b3ecd4b77caf24239401e738
    
    Conflicts:
    	src/com/slim/slimlauncher/Launcher.java
    	src/com/slim/slimlauncher/Workspace.java

commit a356ee08484ddec97a279aff57d436f4ad433ecd
Author: Adam Cohen <adamcohen@google.com>
Date:   Mon Nov 17 17:45:34 2014 -0800

    Add callback which got missed in refactor
    
    Bug 18418855
    
    Change-Id: Ia3a1cec76721bbbc118dd7389b5e960802a64b88

commit c41d36bd46d8de6b986190afc139cccf624bba38
Author: Adam Cohen <adamcohen@google.com>
Date:   Tue Nov 18 17:53:44 2014 -0800

    Prevent multiple workspace state animators from being started
    
    -> Probably an issue with the way we're wrapping ViewPropertyAnimator
       which can lead to us acting like it's valid to have multiple
       instances of a VPA. In reality I think this is very problematic.
    -> For now, we can just make sure the previous animation is canceled
       if it hasn't yet completed.
    
    Bug 18428886
    
    Change-Id: I097eec08ec68ed098e68866fb5eda72734c51b00

commit bef1ce4b50c828fb4a077a6548d46ffc6ca4648b
Author: Adam Cohen <adamcohen@google.com>
Date:   Wed Nov 19 16:03:20 2014 -0800

    Fix a couple regressions from resetting AppsCustomizeTabHost
    
    Bug 18409435
    Bug 18358080
    
    Change-Id: I07a071342b5c5e062ab2bb562b672d93ba0d5c2e
    
    Conflicts:
    	src/com/slim/slimlauncher/AppsCustomizePagedView.java

commit e4cf3eb031c033b19fc764b3c982a2f0c3902d8b
Author: Adam Cohen <adamcohen@google.com>
Date:   Thu Nov 20 14:27:27 2014 -0800

    Updating default page indicator asset
    
    Change-Id: If1be59c8c6590125c2347ba2928f61522f15f959

commit 6596fbe3e789270475697720716663cdc174ae65
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Nov 20 17:01:00 2014 -0800

    Disabling auto addition of managed profile shortcuts
    
    Bug: 16188104
    Change-Id: Ib6464c22140df6d60112eb35f5983718b3db6288

commit 39b08d15b7c55a294bfaeb375cc6342927f652c3
Author: Chris Wren <cwren@android.com>
Date:   Mon Nov 24 16:57:54 2014 -0500

    Don't try to create an app state instance during restore.
    
    Added a static utility function to get the DeviceProfile instead.
    
    Bug: 18504164
    Change-Id: Ia510a84f1c195e58acf3bf4d1f6a42c739fdd413
    
    Conflicts:
    	src/com/android/launcher3/LauncherBackupHelper.java
    	src/com/slim/slimlauncher/LauncherAppState.java

commit 7eaad376e0eb6b6922801c89bfc0a69be7562e6f
Author: Winson Chung <winsonc@google.com>
Date:   Mon Dec 1 15:05:17 2014 -0800

    Ignoring specific db exception to workaround Bug. 18554839.
    
    Change-Id: I80f2dd62297eea671f2d129ae22263e72e506ae4
    
    Conflicts:
    	src/com/slim/slimlauncher/WidgetPreviewLoader.java

commit e5cf48148ca349280a3dd0e4cc60fce877df0eb0
Author: Adam Cohen <adamcohen@google.com>
Date:   Tue Dec 2 15:24:52 2014 -0800

    Ensure that FirstFrameAnimatorHelper doesn't set play time when animation is complete
    
    Bug: 18567716
    
    Change-Id: I656e869b8553d650916c2abe6dc83282c8b6fd65

commit 0a94f287f9ceb7b8706e5c6e4cf208bc0cc16238
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Wed Dec 3 14:25:16 2014 +0530

    Fixing wrong package check when adding shortcuts
    
    Bug: 18571789,18535867
    Change-Id: I2544fa634879846d812b00f8649520400f66d29e

commit f3411f7cb73b986bb9df1fd2eda7a3cb589919e8
Author: Adam Cohen <adamcohen@google.com>
Date:   Thu Dec 4 10:34:57 2014 -0800

    Avoid db exception on L and above
    
    Bug 18554839
    
    Change-Id: I43f391b7cc376f697ce7b5b363e8be3aa85814b5

commit 41135322bcdf74cf915015ce356aca98e2db26da
Author: Griffin Millender <griffinn.millender@gmail.com>
Date:   Tue Apr 28 16:20:44 2015 -0500

    Cleanup after merge

commit 39db00a376b5afe3a18dd63de98e057ca377ee66
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Thu Oct 2 15:58:31 2014 -0700

    Keeping icons in disabled state when SD-card is unmounted
    
    > changing shortcutInfo.isDisabled to be a flag based variable
    > on received OnPackageUnavailable, icons are disabled from desktop
    instead of being removed. Icons in all apps are removed
    
    Bug: 15852084
    Bug: 16238283
    Change-Id: I126d23c709682a917d4bbb84de71032593dce8f9
    
    Conflicts:
    	src/com/slim/slimlauncher/LauncherModel.java

commit 6f2cf2256ffd50e26e4be46bdde7c5fa5c3a2c15
Author: Sunny Goyal <sunnygoyal@google.com>
Date:   Mon Oct 6 16:23:56 2014 -0700

    Updating icons for sortcuts when the target app updates.
    
    Bug: 17398260
    Change-Id: I055abb971d1f72245e8616ac2ce07bcdf37cdd52
    
    Conflicts:
    	src/com/slim/slimlauncher/Launcher.java
    	src/com/slim/slimlauncher/LauncherModel.java
    	src/com/slim/slimlauncher/Utilities.java

commit a49e2c7b6bb85fa4062f0eb0617c307a8dd007b0
Author: Griffin Millender <griffinn.millender@gmail.com>
Date:   Tue Apr 28 17:17:35 2015 -0500

    Updating ItemInfo objects in the worker thread
    
    > Launcher was making non-trivial updates to ItemInfo objects
    on UI thread. These updates were getting skipped when the
    Activity gets destroyed (possibly due to onConfigurationChange)
    > Unregistering SessionCallback on application onTerminate,
    rather than activity onDestroy
    
    Bug: 17941096
    Change-Id: Iad4a50871fe09470f26139b44a2e9886833032f1
    
    Conflicts:
    	src/com/slim/slimlauncher/LauncherAppState.java
    	src/com/slim/slimlauncher/LauncherModel.java

commit 77c67ab9874807a7a1fdbaa3096b3d00f2fec9b3
Author: Griffin Millender <griffinn.millender@gmail.com>
Date:   Tue Apr 28 17:46:22 2015 -0500

    First pass of the Launcher Overlay interface / impl
    
    -> Added simple reference launcher extension
    -> Make launcher able to handle a null qsb
    
    Change-Id: Ib1575243cac800a335e95bbf00cdc394bb4741c3
    
    Conflicts:
    	res/layout-land/launcher.xml
    	res/layout-port/launcher.xml
    	res/layout-sw720dp/launcher.xml
    	src/com/slim/slimlauncher/Launcher.java
    	src/com/slim/slimlauncher/LauncherCallbacks.java
    	src/com/slim/slimlauncher/SearchDropTargetBar.java
    	src/com/slim/slimlauncher/Workspace.java
    
    Conflicts:
    	src/com/slim/slimlauncher/Launcher.java

commit 84fb5517d1cb5a6978c482af511fde484634bfed
Author: Griffin Millender <griffinn.millender@gmail.com>
Date:   Tue Apr 28 17:47:03 2015 -0500

    More cleanup from merge
    
    Change-Id: Ie33208cb52ceef7678e306c1f94f34ff2730aa04

commit 7cabd7deaa2a1f61f2e96bab8395b0b8489d43e7
Author: Griffin Millender <griffinn.millender@gmail.com>
Date:   Tue Apr 28 18:07:26 2015 -0500

    Fix all apps button disappearing
    
    Change-Id: Ibb3c29bdc60d0bf36d640fd70b0ceb9f02c241f8

commit 5ad22b4f98908e630405bccdfa0eb735e172055c
Author: Griffin Millender <griffinn.millender@gmail.com>
Date:   Tue Apr 28 18:26:12 2015 -0500

    Some fixes for overview mode
    
    Change-Id: I792d9723d84fcf45ba6dd2f5346add4fc63d41bb

commit 269703a423e44cce1dcf6f8bcc2731fa6a162d85
Author: Griffin Millender <griffinn.millender@gmail.com>
Date:   Fri Jan 23 00:39:08 2015 -0600

    Fix drawer labels
    
    Change-Id: Ifbeaee592eaac84c3a29200f1b9c13adf9e86688

project packages/apps/Stk/
commit 21fa071f8dc60a91a86cf4f49f81d1bc0e0a133f
Author: Pawit Pornkitprasan <p.pawit@gmail.com>
Date:   Fri Apr 24 13:32:38 2015 +0700

    STK: use single icon as per latest AOSP 5.1
    
    This partially reverts commit b9676c91039df24dfe7bea589bfd277efa1b5b9a.
    and bring some code back in from AOSP 5.1.
    
    Change-Id: I25a76bb95e49ca8effa34332adc1f87b90effb2f

project packages/apps/Terminal/
commit ba5f5805db429d0f88a745fff94f6f5171cb5890
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:15:05 2015 +0300

    Automatic translation import
    
    Change-Id: I6fd61490ff0920ee3f49fc3d773785ebcbd62ab0

project packages/apps/ThemeChooser/
commit ab6137a1851416ac7a36c9fd78d69b6e392af37a
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:15:09 2015 +0300

    Automatic translation import
    
    Change-Id: Ifff863d600291b28f9dda8a5f9f0a2438fb1efb0

commit 3c9f0e11e056993a8b46934d357144e37cfac1c6
Merge: 8ebc84c ab6137a
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:10:47 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

project packages/apps/TvSettings/
commit bb15ca7bf6f9cbe6af7bd3870024df99300954b5
Author: dhacker29 <dhackerdvm@gmail.com>
Date:   Sat Apr 25 22:01:11 2015 -0400

    Add preference for enabling root access
    
    Change-Id: Id0f089ac811c11cb09ae2aa63899e28872f31ed2

commit 57b15c9e2b3a5cafcd4d69df262b82a0b6219cc9
Author: dhacker29 <dhackerdvm@gmail.com>
Date:   Sat Apr 25 20:32:42 2015 -0400

    Ues more descriptive strings for add accessory page
    
    Change-Id: Idafee3ea797bf753c0ada283c2eee0ad29014d7e

commit eaffa731df2a024cf75def2cb61b9568d45247d3
Author: dhacker29 <dhackerdvm@gmail.com>
Date:   Sun Apr 26 22:09:33 2015 -0400

    About: Change the intent to call CMUpdater with Leanback theme (2/2)
    
    Change-Id: I8024fe3325f3651fac59e1266ac34a2ffdc37588

commit ce581cff9a4cf1e1c4f6c372436e1688bd001bc7
Merge: 57b15c9 eaffa73
Author: Abhisek Devkota <ciwrl@cyanogenmod.com>
Date:   Mon Apr 27 19:14:20 2015 +0000

    Merge "About: Change the intent to call CMUpdater with Leanback theme (2/2)" into cm-12.1

commit bc22a11fadc7c29b274a979b909758cb11f439ab
Author: dhacker29 <dhackerdvm@gmail.com>
Date:   Tue Apr 28 01:08:36 2015 -0400

    Accessories: Change max lines to 3 for bluetooth description
    
    Change-Id: I57b91edb852f0366ea34c44bdb0d087866152b1e

commit ab29d3f3f4356df0cd06d63fdb8dbf6a06126975
Author: dhacker29 <dhackerdvm@gmail.com>
Date:   Tue Apr 28 03:29:36 2015 -0400

    Developer Settings: Add setting for updating recovery
    
    When enabled, the recovery of the device will be updated with the
    version of the installed system.
    
    Change-Id: I552293af5bf179227e5ee1163b4653fa00f3261b

commit fa2e1904c4bb73d04b4921486289981442a2160e
Author: dhacker29 <dhackerdvm@gmail.com>
Date:   Tue Apr 28 19:42:06 2015 -0400

    Developer Settings: Add warning to request root access
    
    And ensure properties are reset when disabling adb root
    
    Change-Id: I9751725cbabe69f6497b18e92acd6387d6a9ce91

project packages/apps/UnifiedEmail/
commit 8110c1275a7a03099335a3aa2e4a59fa3376d6a9
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:15:13 2015 +0300

    Automatic translation import
    
    Change-Id: I1446ab9b8e1e5c9e87c97ebd38a2e596e381724d

commit 865682e1f7b6abb80d001567b69bdb9f965f1fea
Merge: 2bba20c 8110c12
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:11:20 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

project packages/services/Telecomm/
commit ef6be14d04fb8741e73d0f1c0cf7c7b428f8e84c
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:16:03 2015 +0300

    Automatic translation import
    
    Change-Id: Ib61c8d1616070c5eb2d76bcc7373d6e42d66650d

commit e4b451a18cca714db1dd306ace45b477c2b543f9
Merge: 446e65b ef6be14
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:09:51 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

project packages/services/Telephony/
commit d57df97ad4b30b578b9a2dcd105261e43486c870
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:16:09 2015 +0300

    Automatic translation import
    
    Change-Id: I306a9c55d486933a7ab343a0f08da88d93719019

commit 11ce1e8f25f3c22da1e8695145bb5b93b5f5bad0
Merge: 7e68590 d57df97
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 18:10:23 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

commit a4c8700f51517afdee390ff7090cce38b47ecad9
Author: mengsun <msun@codeaurora.org>
Date:   Wed Dec 11 17:56:42 2013 +0800

    TeleService: Add a controller for in-call proximity sensor (3/3)
    
    Add the setting for enable proximity sensor or not when calling
    
    ps2: Enable via overlay
    
    Change-Id: I42bc05ae1c22443cca782ac1ae66d5d5bb4ac858
    
    Conflicts:
    	src/com/android/phone/CallFeaturesSetting.java

commit 13d7fb84da237e793cf9527f15e469dd612b6b9c
Author: Lin Ma <lma@cyngn.com>
Date:   Mon Mar 30 17:38:33 2015 -0700

    TeleService: pass phone ID to APN setting
    
    Conflicts:
    	src/com/android/phone/CdmaOptions.java
    
    Change-Id: I3df6c42bc97a68f9e58431e0585a957056912e37
    
    Patchset: 2
    http://review.cyanogenmod.org/#/c/96439/

commit 1a58b65756903c3f89af8f8afdb4c878645c69e7
Author: LuK1337 <priv.luk@gmail.com>
Date:   Wed Apr 29 13:31:53 2015 +0200

    msim: Fix FC on opening "calling accounts" in Dialer settings
    
    Variable sir seems to be null on some msim devices.
    
    Change-Id: Ia046e04da2edc0c06ed91a5878111f8e98f23b3b

commit 96e25bf7c4ccbd9f53b9159845c1d6c24c8f020a
Author: cretin45 <cretin45@gmail.com>
Date:   Thu Apr 23 12:25:12 2015 -0700

    TeleService: Remove HomeAsUp arrow for nested pref screens
    
    This brings the msim settings in line with single sim.
    
    Change-Id: I968efb7abcb8cfe85bff5593ac95794d6879a8b6

project packages/wallpapers/PhotoPhase/
commit 5b9c27711b3be1d3f672021def92e8cc8289dae6
Author: Michael Bestas <mikeioannina@gmail.com>
Date:   Sat Apr 25 01:16:16 2015 +0300

    Automatic translation import
    
    Change-Id: I8ec494a96a372d7168882d2e4e5a0587f21efd7f

project prebuilts/ndk/
commit 9c744e25e9288ef771c5f072b917e905ba144e66
Author: ZION959 <ziontran@gmail.com>
Date:   Sun Apr 26 14:45:47 2015 -0700

    fixed buidld for clang qcom 3.6
    
    Change-Id: I6d516fd6edd6d51bec2cdb389cf731f96e2dbf55

project system/core/
commit a62d6161bb5a6ee55cd4ac9ccd3fe929b291bafb
Merge: 00a598a 01e3a95
Author: ZION959 <ziontran@gmail.com>
Date:   Sat Apr 25 17:48:54 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

commit 35493c4c327406a46c32a219db4be30cad5a0256
Author: Danny Baumann <dannybaumann@web.de>
Date:   Mon Apr 20 17:19:46 2015 +0200

    Disable backlight when blanking panel.
    
    This used to be the behaviour up to and including cm-11.0 (see e.g.
    commit f7ce72ca), but in newer versions the backlight is only turned on
    and never off (see commit 1e961c04). Fix it.
    
    Change-Id: I6c3bf6abbb4e11dc010c360ecfe9f3bb3e2f3548

commit 3070e37c91b673b4833ec05d0f9b3341ef6d5347
Merge: a62d616 35493c4
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 19:20:27 2015 -0700

    Merge remote-tracking branch 'CM/cm-12.1' into cm-12.1

project system/extras/
commit 440188e143e77c6521a5f10d48d632d83c300c9a
Author: David Ferguson <ferguson.david@gmail.com>
Date:   Thu Jun 7 21:00:41 2012 -0400

    ext4_utils: add BoardConfig define to suppress EMMC-corrupting wipe command
    
    If BOARD_SUPPRESS_EMMC_WIPE is true, the EMMC wipe command will not be
    issued. This works around a bug in some firmware revisions of Samsung EMMC's
    that permanently damages the device when the wipe command is issued.
    
    For affected devices with kernel source, MMC_CAP_ERASE should be removed
    from the kernel instead.
    
    This is only part of the solution but it does handle the "flashing CM9
    for the first time on an unsafe kernel" situation.
    
    Change-Id: Ie4e31f9268a65218e5d344ae3068b021790fc33c

commit 31fe061daac530269120c70540f17109a898f934
Author: Arne Coucheron <arco68@gmail.com>
Date:   Sun Apr 26 01:19:37 2015 +0200

    ext4_utils: Fix build
    
     * include $(BUILD_EXECUTABLE) was listed twice.
    
    Change-Id: Id1c7f5d588d70126035409dff87f6caf599eba64

commit 972c9f1a7fd2602786bca7ca73ad04414edf5ee8
Author: Andrew Dodd <atd7@cornell.edu>
Date:   Fri Jul 27 08:40:53 2012 -0400

    ext4_utils: Fix bad merge of EMMC wipe suppression
    
    The order of the modules in the Makefile changed.
    
    The Makefile items for eMMC wipe suppression should be
    in the sections for target static and dynamic
    libext4_utils.  These were the first two modules in the
    file previously, but no longer are.
    
    Move the eMMC wipe configuration handling to the proper
    modules.
    
    Change-Id: I86861a89824af04a3b08e75049580df28bd239f7

project vendor/cm/
commit 3393dab46fa48b6465e732e1e7b7ff89f7846627
Author: luca020400 <luca.stefani.ge1@gmail.com>
Date:   Fri Apr 24 18:10:22 2015 +0200

    vendor:cm: fixup formatting of CONTRIBUTORS
    
    Change-Id: I79e96edbf5dd69053297473964c73f71be86568d

commit 52f92f081d793fc7cf715512e69c0a285e41a76d
Author: Roman Birg <roman@cyngn.com>
Date:   Mon Apr 20 18:20:59 2015 -0700

    add Profiles to build
    
    Change-Id: Id74a2c5350a5140eeb6f83c950c8b9ed89b2d4d7
    Signed-off-by: Roman Birg <roman@cyngn.com>

commit 17e5661017b955131f828ad37dbb65414e71ed6b
Author: dhacker29 <dhackerdvm@gmail.com>
Date:   Sat Apr 25 02:03:49 2015 -0400

    overlay: Remove the default battery style and set it in frameworks
    
    This will allow us to remove the overlay in vendor/cm so devices
    with no battery, aka fugu, can override this to none.
    
    Change-Id: I80c0cc06d3aed344c7c705d420af297c96baf706

commit 70d7e18828953d43381e7e7a0dc70d74ae10ba35
Author: Ricardo Cerqueira <ricardo@cyngn.com>
Date:   Mon Apr 27 15:06:49 2015 +0100

    Kill spn-conf overrides
    
    These were overloading the ASCII names to region-specific charsets,
    which looks nice but it's horribly confusing if you're not native
    from those regions and happen to be roaming there.
    
    So... like our upstreams, just show the original carrier names
    
    Change-Id: Icb3c6c9be2a4ee57866f2f57411a4f441be88f7c

commit 1a2f28834883f6673c3888f7a8440bab4954f81a
Author: Howard M. Harte <hharte@cyngn.com>
Date:   Wed Apr 15 10:47:36 2015 -0700

    Update APNs for Smartfren
    
    Change-Id: Id46a069af6e4b01b8c39ce82342043633b6168c0

commit bd713559242dc70bea35bc750db69ef8f890d273
Author: Howard M. Harte <hharte@cyngn.com>
Date:   Fri Apr 24 16:26:49 2015 -0700

    Update Smartfren APN protocol to IPV4V6
    
    Change-Id: I30384d45cf184253ca6ef4ce8847fe80228a012a

commit d1757405805a356bb68b7e099ee5d1b87da33101
Author: Erica Chang <echang@cyngn.com>
Date:   Thu Apr 9 10:20:03 2015 -0700

    SIM card setting: fixed Smartfren SPN override name
    
    Change-Id: I5b5798516ae2620d9fa544470bc107421f12173e
    (cherry picked from commit 623bc5bb1c80ff7dd8a3cd9c4b8272dfd8453db1)

project vendor/cmremix/
commit 9767563e9ac66dfc70482a9776c567e0a0634a5e
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Fri Apr 24 02:26:56 2015 -0700

    Fix bluetooth in SaberMod ARM Mode
    
    Change-Id: I48813e65a33f663c5f6b67710859d309063234db
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit b2888f35a98729bab91d67826390634066b2a276
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sat Apr 25 01:59:04 2015 -0700

    Make SaberMod ARM Mode enabled by default and use 4.9 for hammerhead:
    Now that bluetooth is fixed when SaberMod ARM Mode is enabled, I
    see no reason why this shouldn't be default.  SaberMod ARM Mode also
    fixes other bugs, that allow gcc 4.9 for the ROM to function with force
    closes of setup wizard.
    
    Change-Id: I6ac2e9d0f5371a95b13786ab01989096a0da351b
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 62d8b1bd8d57f95bf485bdb34ca1276fff036a5c
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sat Apr 25 01:36:42 2015 -0600

    sm.mk: more dependency fixes:
    
    I see no benifit to loop optimizations on arm thumb mode.
    
    Change-Id: Ia1f49ffe7ad7462e80c4add44abb5606ff6c915d
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit be977aae7cbf802016a9944edd1ed38f43b6e0f9
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Sat Apr 25 02:07:34 2015 -0700

    small cleanup
    
    Change-Id: Iade992780810c8cb2cd23d8e9586910debdd2980
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	products/sm_hlte.mk

commit a80ed73f99c5ed6f262deb2cec9428b21d0e4727
Author: ZION959 <ziontran@gmail.com>
Date:   Sun Apr 26 19:18:40 2015 -0700

    enabled clang qcom 3.6 and fixed bluetooth UNINITIALIZED

commit ea28b1de21c273f050a9a83a7d1653c3cecd8c64
Author: Your Name <you@example.com>
Date:   Mon Apr 27 17:29:21 2015 +0200

    add Sony Xperia Z Ultra (togari)

commit 7ae8e1456e2a4452b3204495d910cb3625c76f0c
Author: Your Name <you@example.com>
Date:   Mon Apr 27 17:39:54 2015 +0200

    added libqsap_sdk to LOCAL_BASE_DISABLE_STRICT_ALIASING so togari can compile

commit 44ba763d27832117c0fea31305c824fcc18f1504
Merge: a80ed73 7ae8e14
Author: ZION959 <CMRemix@users.noreply.github.com>
Date:   Mon Apr 27 09:14:40 2015 -0700

    Merge pull request #2 from mustermaxmueller/cm-12.1
    
    add Sony Xperia Z Ultra (togari)

commit 9af64763461e5ecf20844da06aab19a565e6fb85
Author: ZION959 <ziontran@gmail.com>
Date:   Mon Apr 27 13:49:34 2015 -0700

    update Sony Togari to be inline with SaberMod Optimization

commit bdca3e9f63f195909225855535ee0d78eedcea55
Author: ZION959 <ziontran@gmail.com>
Date:   Mon Apr 27 18:20:43 2015 -0700

    change kernel dependencies for trltespr

commit 9d835a583eca69e098adadab0e78e2b4b3e23ae8
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Mon Apr 27 16:05:30 2015 -0700

    Update changes from build
    
    Change-Id: I82e8efffee4589bb7dcd1add6545ae1e749859cc
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	config/cmremix_sm.mk
    	products/sm_hlte.mk

commit d387b02b5cb978cfde5e8f961ca5795502c24f2b
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Mon Apr 27 03:23:56 2015 -0600

    Remove flag -fprefetch-loop-arrays
    
    Change-Id: I4ab35836b460c20d75bcc2e08fdb6a194c1b9064
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 81558032eef8ae5aa151945cdc9246d73bea086a
Author: ZION959 <ziontran@gmail.com>
Date:   Tue Apr 28 02:33:37 2015 -0700

    sm.mk : disabled bunchs of violate strict aliasing modules for CM-12.1 Base

commit 9be9c8c6e43dd219a704da31e62df0f6b058a933
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Tue Apr 28 13:36:53 2015 -0700

    Add a option to disable vectorization flags for bluetooth (1/2)
    
    Change-Id: I90f1e2489d16096401000b00d530805db470a32b
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	config/cmremix_sm.mk

commit 02a3112c45ba1d05642cc606d80eb716580abef1
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Wed Apr 29 13:00:34 2015 -0600

    Fix bluetooth crashing when using -O3 optimizations
    
    Force -Os
    
    Change-Id: I497cbdd5f52dbd24b7acc1f1ffe165eff3d6e4dd
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit 3a8b05a5be7311c239eb5108f69bc85e0d438788
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Wed Apr 29 23:12:23 2015 -0600

    Remove extra kernel gcc version info writing to build.prop (2/2)
    
    No longer needed with
    https://gitlab.com/SaberMod/pa-android-packages-apps-settings/commit/9590f426e7986e64d68ae80b4ac5c6409f4c88b5
    
    Change-Id: Icc3722b2f453f74c9aadde7998cf0faab35f7230
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>

commit b0e6ca7a43a1943ce35f32bfb3d56690580e773d
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Thu Apr 30 10:13:45 2015 -0700

    Add strict-aliasing for optimization options.
    
    Change-Id: I903132993e75cfce35cee8ba1d21f1f6725322f1
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	config/cmremix_sm.mk

commit 3f095d85423846ece708c82024d97ef02da071c1
Author: Paul Beeler <pbeeler80@gmail.com>
Date:   Thu Apr 30 10:15:58 2015 -0700

    Fix bluetooth for good! (1/2)
    
    Change-Id: Ia09b64351cb6b5a2353160252567f83e10d38690
    Signed-off-by: Paul Beeler <pbeeler80@gmail.com>
    
    Conflicts:
    	config/cmremix_sm.mk

commit 4a531d59b781160753f1fed38231d912e857cf17
Author: ZION959 <ziontran@gmail.com>
Date:   Fri May 1 00:22:12 2015 -0700

    clean up

project vendor/samsung/
commit 5274eeaf94e68f3d63e93c0d69cd5bd51fe3f558
Author: Tony Layher <layhertony@gmail.com>
Date:   Sat Apr 25 17:03:35 2015 -0400

    trlte-common: Update camera HAL for 12.1
    
    Change-Id: Ic78228e72c4e5282b26911695fad25c9d5428cbf

commit 706db98f915a8d6bc57c87f55bd83bb0ac2f28dd
Merge: 0401727 5274eea
Author: ciwrl <ciwrl05@gmail.com>
Date:   Sat Apr 25 14:04:55 2015 -0700

    Merge pull request #609 from slayher/cm-12.1
    
    trlte-common: Update camera HAL for 12.1

commit 44cb70e178058a7894f4831605799eafedce95e8
Merge: 706db98 d564cd6
Author: Arne Coucheron <arco68@gmail.com>
Date:   Sun Apr 26 05:55:54 2015 +0200

    Merge pull request #610 from arco/cm-12.1
    
    serrano: Adreno blobs from Flo LMY47O

commit ea5f4eec1ca017bb68aa44ece8bda5b460674f7d
Author: Dave Daynard <nardholio@gmail.com>
Date:   Tue Apr 28 21:00:02 2015 -0400

    d2gsm: Use rilblobs from AT&T NJ1 release
    
    Change-Id: I390995911423d7c28995e9d4ebfa76f171d11922

commit 446757d8460406a6a486fc85fedd1351425337a2
Author: Dave Daynard <nardholio@gmail.com>
Date:   Tue Apr 28 21:14:16 2015 -0400

    d2-common: update camera firmware
    
    Change-Id: I462cc98c9e3e735adc3c9005dcd165ef1bfb3250

commit d33393e2226c6e4b042b8cc62db1549e1460b2a2
Merge: 44cb70e 446757d
Author: Shareef Ali <shareefalis@cyanogenmod.org>
Date:   Tue Apr 28 21:21:13 2015 -0400

    Merge pull request #611 from nardholio/cm-12.1
    
    update d2 blobs