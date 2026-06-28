# Third-Party Notices — KeyAxis

KeyAxis is free software. It bundles or uses the third-party components listed
below. Their copyright notices and license terms are reproduced here as required
by their licenses. (KeyAxis itself is an unofficial tool — see the disclaimer at
the bottom.)

---

## 1. vJoy — virtual joystick driver, `vJoyInterface.dll`, and the vJoy installer

- Copyright (c) 2017 Shaul Eizikovich
- License: **MIT License**
- Source: https://github.com/shauleiz/vJoy

```
MIT License

Copyright (c) 2017 Shaul Eizikovich

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

> Note: if you bundle a vJoy build from a different fork/source than the official
> repo above, verify that build's own license and include its notice instead.

---

## 2. Qt for Python (PySide6) and the Qt libraries

- Copyright (c) The Qt Company Ltd and other contributors
- License: **GNU Lesser General Public License v3 (LGPLv3)** — which incorporates the
  GNU General Public License v3 (GPLv3) by reference
- License texts: https://www.gnu.org/licenses/lgpl-3.0.html and
  https://www.gnu.org/licenses/gpl-3.0.html
- Qt for Python licensing: https://doc.qt.io/qtforpython-6/licenses.html

KeyAxis uses Qt only through PySide6 as dynamically-loaded shared libraries under
the LGPLv3; KeyAxis does not modify Qt. As permitted by the LGPLv3, you may obtain
the full license texts at the URLs above and you may replace the bundled Qt /
PySide6 components with your own compatible build. For the materials needed to
relink, contact the KeyAxis author.

---

## 3. qt-material — Material Design stylesheet for Qt

- Copyright (c) Yeison Cardona
- License: **BSD 2-Clause "Simplified" License**
- Source: https://github.com/dunderlab/qt-material

```
BSD 2-Clause License

Copyright (c) Yeison Cardona

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

> The exact copyright year is as stated in the upstream `LICENSE` file at the
> source repository above.

---

## 4. Python (interpreter, standard library incl. tkinter / ctypes)

- Copyright (c) 2001-present Python Software Foundation. All Rights Reserved.
- License: **Python Software Foundation License (PSF)** — a permissive license
- Full text: https://docs.python.org/3/license.html

---

## 5. PyInstaller (build tool / bundled bootloader)

The standalone `KeyAxis.exe` includes the PyInstaller bootloader. PyInstaller is
licensed under **GPL 2.0-or-later with the "bootloader exception"**, which
explicitly permits distributing the bundled application under a license of your
own choosing (it does not impose the GPL on the bundled app).

- https://github.com/pyinstaller/pyinstaller (see `COPYING.txt`)

---

## Trademarks / disclaimer

DCS World, Eagle Dynamics, Heatblur, Thrustmaster, and other product names are
trademarks of their respective owners and are used only for identification.
**KeyAxis is an unofficial, independent tool and is not affiliated with, endorsed
by, or sponsored by any of them.** KeyAxis is provided "as is", without warranty,
used at your own risk.
