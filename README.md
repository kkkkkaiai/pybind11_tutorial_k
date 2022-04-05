# Demo of pybind11

## Compile

```bash
cmake .. \
-DPYTHON_LIBRARY_DIR="/home/znfs/anaconda3/envs/detectron2/lib/python3.6/site-packages" \
-DPYTHON_EXECUTABLE="/home/znfs/anaconda3/envs/detectron2/bin/python3"

make -j10
make install
```

## Performance test
```bash
python performance_test.py p 1  # p=python
python performance_test.py c 1  # c=c++
```


## Reference
https://cloud.tencent.com/developer/article/1919872 \
https://github.com/tdegeus/pybind11_examples \
https://github.com/smrfeld/cmake_cpp_pybind11_tutorial \
https://github.com/smrfeld/advanced_pybind11_features 
