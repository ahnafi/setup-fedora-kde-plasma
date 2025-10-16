# Install FFMPEG nonfree

Step 1: Enable RPM Fusion repositories
If you haven't already, enable the RPM Fusion repositories. The non-free repository is usually empty, so enabling both the free and non-free repositories is a standard practice.
bash

```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

Step 2: Swap ffmpeg-free for ffmpeg
After enabling the repositories, use dnf swap to replace the default ffmpeg-free with the ffmpeg package from RPM Fusion. The --allowerasing flag is necessary to remove any conflicting ffmpeg-free packages.
bash

```bash
sudo dnf swap ffmpeg-free ffmpeg --allowerasing
```

Step 3: Verify the installation
After the swap is complete, you can verify the installation by checking the version of ffmpeg:
bash

```bash
ffmpeg -version
```

If the command runs without errors, ffmpeg is successfully installed with the non-free codecs.
