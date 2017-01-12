#保存图片
fig = plt.figure()
plt.savefig(name,dpi=fig.dpi)

#转化图片格式 --> bmp 256色
```python
import os
from PIL import Image
import glob
for dir in os.listdir(os.getcwd()):
    for filename in glob.glob(dir+'/*'):

        if filename.endswith('.bmp'):
            # Destroy Previously Converted BMP
            try:
                os.remove(os.path.join(dir_path, filename.replace('.jpg', '.bmp')))
            except:
                pass
        elif filename.endswith('.jpg'):

            # Open Image
            im = Image.open(filename)

            # Quality Control
            # im.save(os.path.join(dir_path, filename), quality=-50)

            # What if the world had a set number of colors
            im = im.convert(mode="P", palette=Image.ADAPTIVE, colors=256)

            # To bmp
            #im = im.convert("RGB")

            # Thumbnail
            #im.thumbnail(size)

            # Print Shop Deluxe
            im.save('..\\bmp256\\'+filename.split('\\')[-1].replace('.jpg', '.bmp'))
```
#画等高线
  plt.contour(x,y,z) z是2维, x,y可以是1维可以是2维 , 具体使用见sklearn包函数 svm.py
