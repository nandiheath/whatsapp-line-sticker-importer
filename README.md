# whatsapp-line-sticker-importer
This is a nodejs script that run on Mac to export the line stickers within an Android device and easily import to [whatsapp sticker project](https://github.com/WhatsApp/stickers/tree/master/Android)

# Preliminary
Please install webp and npm before executing this script

- brew install webp
- brew install npm

# How To Use

First export the stickers folder from your android device.
Usually it is located at 
```
/Android/data/jp.naver.line.android/stickers
```

Copy it to your mac, and then run the script

```
# checkout the script
git checkout https://github.com/nandiheath/whatsapp-line-sticker-importer.git

cd whatsapp-line-sticker-importer

# install the dependencies
npm install

# Run the script with params
./sticker-exporter export -n MySticker1 -p AuthorName /path/to/single/sticker/folder/ ./destination_folder
```

The script will copy all the images from the source folder and resize it automatically to what whatsapp needed. And there will be a "contents.json" file created inside the destination folder.

Move the destination folder to whatsapp sticker project

```
mv destination_folder /path/to/whatsapp/stickers/Android/app/src/main/assets/
```

Copy the content inside the contents.json inside the destination folder, and add it to the sticker_packs.stickers array inside /path/to/whatsapp/stickers/Android/app/src/main/assets/contents.json

```
{
  "android_play_store_link": "",
  "ios_app_store_link": "",
  "sticker_packs": [ {
    ...
  },
    // <=== paste it here
  ]
}

```

Build the project and you can see your line stickers are there. Enjoy!
