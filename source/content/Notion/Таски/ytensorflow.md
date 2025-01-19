---
Created: 2022-11-09T15:23
---
- запускаем докер с нужным окружением на v100, или другой тачке с рут доступом  
    (иначе почему-то apt не работает, а пакеты которые ставит brew почему-то валятся на компиляции(не видит куски standart libc как будто бы), хотя версии те же. Вероятно ошибка где-то в PATH но как фиксить не вкурил)  
    
- install deps

```undefined
apt update && apt install protobuf-compiler gcc-7 g++-7
pip install -U pip setuptools cython
```

- fix bad cuda symlink

```JavaScript
rm /usr/local/cuda
ln -s /usr/local/cuda-11.4 /usr/local/cuda
```

- comment version checking in [setup.py](http://setup.py) func locate_cuda(226-233 lines in my version), in new version we dont have version.txt, version could determine via {/usr/local/cuda-11.4/bin/nvcc —version}
- if script dont work for revision you can take it via {arc log -n 500} and fix setup.py
- compile with options

```Bash
python setup.py bdist_wheel --with-cuda --without-opencv --revision={revision} --tensorflow-version=1.15.2 --cuda-version=11.4 --cuda-directory=/usr/local/cuda
```