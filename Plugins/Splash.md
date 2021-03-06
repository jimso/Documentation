# Splash

Small (4k), simple plugin that lets you throw up a splash screen in NSIS installers.

## Usage

    Function .onInit
      SetOutPath $TEMP
      File /oname=spltmp.bmp "my_splash.bmp"

    ; optional
    ; File /oname=spltmp.wav "my_splashsound.wav"

      splash::show 1000 $TEMP\spltmp

      Pop $0 ; $0 has '1' if the user closed the splash screen early,
         ; '0' if everything closed normally, and '-1' if some error occurred.

      Delete $TEMP\spltmp.bmp
    ;  Delete $TEMP\spltmp.wav
    FunctionEnd


Note that the first parameter to splash.exe is the length to show the
screen for (in milliseconds), and the second is the splash bitmap filename (without
the .bmp). The BMP file used will be this parameter.bmp, and the wave file used
(if present) will be this parameter.wav.

(If you already have an .onInit function, put that in it)

Note: the return value of splash is 1 if the user closed the splash 
screen early (pop it from the stack)

## Credits

Written by Justin Frankel and [Amir Szekely][1].

[1]: http://nsis.sourceforge.net/User:Kichik
