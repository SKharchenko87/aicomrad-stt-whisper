

```bash
mkdir -p models
cd models
wget https://raw.githubusercontent.com/ggml-org/whisper.cpp/master/models/download-ggml-model.sh
chmod +x download-ggml-model.sh
./download-ggml-model.sh large-v3-turbo
cd ..
```


```bash
mkdir -p build
cd build/
cmake .. -DGGML_CUDA=ON
cmake --build . -- -j$(nproc)
cd ..
```

```bash
./build/whisper_service  --model models/ggml-large-v3-turbo.bin --port 9090
```
или 

```bash
sudo cp ./whisper_service.service /etc/systemd/system/whisper_service.service
sudo systemctl start whisper_service.service
systemctl enable whisper_service.service
```
