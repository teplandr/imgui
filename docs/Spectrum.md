# ImGui-Spectrum
The goal of this project is to provide the ease of use and quick C++ development of the ImGui library, while also embracing Adobe's Spectrum guidelines, thus giving a similar look and feel to Adobe's flagship products. 

This project aims at not changing the ImGui API at all, so you could swap between ImGui and ImGui-Spectrum without changing your code. 

ImGui-Spectrum is currently usable, but adaptation of Spectrum widgets is not fully complete. Everything is fully functional, but some widgets may not look like the Spectrum ones. It currently looks like this:

![example](https://git.corp.adobe.com/storage/user/21980/files/4a645748-bc24-11e8-85be-70a4dfe3d4ca)

## Using Imgui-Spectrum

### Moving from original ImGui to ImGui-Spectrum
This repository has exactly the same API as the original ImGui. You should be able to just swap to this without any issues. Keep in mind ImGui changed a bit in the last releases, and you may have to update accordingly.

* If you just copied ImGui source files to your project, you can overwrite them with the files from this repository. Make sure to include `spectrum.h`.
* If you are using ImGui as a submodule, you can change the remote url in your `.gitmodules` file and then run `git submodule sync`.

### Getting started with ImGui or moving from another GUI library
To be added. For an introduction please read ImGui's README, and feel free to contact me.

### Using Spectrum in your code
Make sure you are using the default theme by calling `ImGui::StyleColorsClassic();` in your application. You can change from Light to Dark theme, check `spectrum.h`.

You can add the AdobeClean font that you can [download here](http://spectrum.corp.adobe.com/fonts.html) with the following code:
```
ImGuiIO& io = ImGui::GetIO();
io.Fonts->AddFontDefault();
ImFont* font = io.Fonts->AddFontFromFileTTF("../AdobeClean-Regular.ttf", 16.0f);
if (font) io.FontDefault = font;
```
As a reminder, AdobeClean is a [restricted font](https://www.adobe.com/products/type/font-licensing/restricted-fonts.html).


## Compiler
ImGui should be compatible with a wide array of C++ compilers. ImGui-Spectrum is using the C++11 feature `constexpr` in `spectrum.h`. If you cannot use C++11 you can remove the `constexpr` keywords from there.


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


## Planned features
Planned features include:
* Better controls, fixing the shortcomings above.
* More buttons types. Spectrum has many: Call-To-Action, Primary, Primary (quiet), Secondary, Secondary (quiet), Negative. 
* A Window (ImGui::Begin() .. End() pair) to create standard sidebar / header bar / panel.

In general, the plan is to *not* add the full range of Spectrum controls and their variations, but just enough to make a good looking C++ prototype application. 


## For ImGui-Spectrum developers
### Internal Changes
* Added spectrum.h with spectrum colors under `namespace Spectrum`.
* Added RenderFrameBorder that takes border color and size
* Added RenderFrame that takes border color
* Added color parameter to RenderText, RenderTextWrapped, RenderTextClipped

The above functions are likely to cause merge issue in the future if ImGui's author decides to refactor them as planned.

### How to update 
After ImGui releases, pull changes with `git pull ocornut-origin master`. Merge eventual conflicts, then `git push` as usual.

If you don't yet have the original remote in your local copy, you can add it with `git remote add ocornut-origin https://github.com/ocornut/imgui.git`
