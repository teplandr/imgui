## Using Imgui-Spectrum
Depending on whether you are moving from an existing ImGui project or starting new, read one of the following sections, then keep reading for more usage details!

### Moving from original ImGui to ImGui-Spectrum
This repository has exactly the same API as the original ImGui. You should be able to just swap to this without any issues. Keep in mind ImGui changed a bit in the last releases, and you may have to update accordingly.

* If you just copied ImGui source files to your project, you can overwrite them with the files from this repository. Make sure to include `spectrum.h`.
* If you are using ImGui as a submodule, you can change the remote url in your `.gitmodules` file and then run `git submodule sync`.

### Getting started with ImGui or moving from another GUI library
to be added - sorry!

### Using Spectrum in your code
Make sure you are using the default theme by calling `ImGui::StyleColorsClassic();` somewhere in your application. 

You can add the AdobeClean font that you can download here (http://spectrum.corp.adobe.com/fonts.html) and the following code:
```
io.Fonts->AddFontDefault();
ImFont* font = io.Fonts->AddFontFromFileTTF("../AdobeClean-Regular.ttf", 16.0f);
if (font) io.FontDefault = font;
```

You can change from Light to Dark theme, check `spectrum.h`.


## Compiler
ImGui should be compatible with a wide array of C++ compilers. In the Spectrum port I introduced C++11 restriction with `constexpr` in `spectrum.h`. If you cannot use C++11 you can remove the `constexpr` keywords from there.


## Controls
* Button - matches Spectrum's Action button. Other buttons to be added (call to action, primary).
* Checkbox - ok
* Radio - ok
* Combo - not adapted. Need work on Selectables and overall look.
* Input - more or less ok
* Drag and slider controls do not match Spectrum, but would be a pain to do since each is coded individually (int, float, etc). 
* Scrollbar - colors ok, Spectrum's bar is smaller when not active.
* Resize control - Spectrum doesn't have one (?), matches scrollbar colors.
* Collapsing Header - Spectrum doesn't have this, but it is a common feature of ImGui. Implemented, inspired by Spectrum's Call-To-Action button. 


## Internal Changes
* Added spectrum.h with spectrum colors under `namespace Spectrum`.
* Added RenderFrameBorder that takes border color and size
* Added RenderFrame that takes border color
* Added color parameter to RenderText, RenderTextWrapped, RenderTextClipped


## For maintainers: how to update 
After ImGui updates, pull changes with `git pull ocornut-origin master`. Merge eventual conflicts, then `git push` as usual.

If you don't yet have the original remote you can add it with `git remote add ocornut-origin https://github.com/ocornut/imgui.git`
