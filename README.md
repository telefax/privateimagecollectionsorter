# privateimagecollectionsorter
Two commands to manage the a digital private photo collection based on Exif dates.


I'm running this on a CentOS 8 which has my NAS mounted over NFS.

## Install tools needed
```yum install perl-Image-ExifTool.noarch fdupes```



## In this directory you will trow in all images you want sorted, just throw your whole phone into it or whatever
```mkdir /mnt/nas/imagearchive/incoming```

## This is the directory that all images will be moved into once sorted.
```mkdir /mnt/nas/imagearchive/years```

Final format for sorted images will be like this:

years/2013/2013-03/2013-03-24_17h38m48s_631.jpg


## How to sort and remove dupes (recursive/noprompt/delete).
It will run through your entire collection and remove duplicate files, it'll take forever.

```cd /mnt/nas/imagearchive/ && fdupes -r -N -d .```

Do the sorting, still in the imagearcive root
```exiftool '-Directory<CreateDate' -d years/%Y/%Y-%m -r incoming/```
