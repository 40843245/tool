# Tex Live
## installation
1. Visit [TeX Live (official website)](https://www.tug.org/texlive/windows.html)
2. According to OS of your device, click the corresponding link.
3. Under `Content` (which indicates TOC which stands for `table of content`), click `Easy install` link.
4. Under `Easy install` section, click `install-tl-windows.exe` link, it will download the installation exe `install-tl-windows.exe`.
5. Click installation exe `install-tl-windows.exe` to download `Tex Live`.

> [!WARNING]
> It may takes a lot of time to download `Tex Live` by click installation exe `install-tl-windows.exe`. The main reason is
>
> +
> ```
> The TeX Live distribution already contains compressed archives (.tar.xz) and these are used for installation. The reason why it is slow is that there are a lot packages, and for each there are between 1 and 4 archives to be downloaded, decompressed (xz), and unpackaged (tar).
> ```
> +
> ```
> there is no multi-threaded installation, so the packages are done one-by-one and not in parallel.
> ```
>
> Thanks to [norbert's answer on stackoverflow](https://tex.stackexchange.com/questions/527364/why-texlive-installation-is-so-slow#:~:text=The%20TeX%20Live%20distribution%20already%20contains%20compressed%20archives,to%20be%20downloaded%2C%20decompressed%20%28xz%29%2C%20and%20unpackaged%20%28tar%29.)
