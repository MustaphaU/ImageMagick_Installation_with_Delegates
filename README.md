# Install ImageMagick with Delegates on WSL2

### 1. Remove Existing ImageMagick Packages

```sh
sudo apt remove imagemagick imagemagick-6.q16
```

### 2. Update Package Lists

```sh
sudo apt-get update
```

### 3. Install Delegate Libraries

```sh
sudo apt-get install \
    libwebp-dev libopenjp2-7-dev librsvg2-dev libxml2-dev \
    libfontconfig1-dev libfreetype6-dev liblcms2-dev libexif-dev \
    libopenexr-dev libheif-dev libraw-dev libfftw3-dev liblqr-1-0-dev
```

### 4. Download and Extract ImageMagick

```sh
wget https://www.imagemagick.org/download/ImageMagick.tar.gz
tar xvzf ImageMagick.tar.gz
```

### 5. Build and Install

```sh
cd ImageMagick-*
./configure
make
sudo make install
sudo ldconfig /usr/local/lib
```

---

## Verify Install

### Check ImageMagick Version

```sh
magick --version
```

### List Enabled Delegates

```sh
magick -list configure | grep DELEGATES
```

### Test: Create a Sample Image

```sh
magick -background lightblue -fill yellow -font AvantGarde-Book -pointsize 72 label:Helloworld helloworld.png
```


