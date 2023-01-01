This repo contains artifacts and configurations to use the Triton Model Analyzer.

## Instructions

1. Clone the model analyzer repo.
```
    git clone https://github.com/triton-inference-server/model_analyzer.git -b r22.10
```
2. Build a container via instructions [here](https://github.com/triton-inference-server/model_analyzer/blob/main/docs/install.md#specific-version-with-local-launch-mode).
```
    cd ./model_analyzer
    docker build --pull -t model-analyzer .
```
3. Clone this repo.
```
    git clone TBD
    cd model_analyzer_experiments
```
4. Launch the model analyzer container with these paths. Add `--gpu=all` when available.
```
    docker run -it --rm \
        -v $(pwd)/config:/config \
        -v $(pwd)/models:/models \
        -v $(pwd)/export:/export \
        -v $(pwd)/output:/output \
        --net=host model-analyzer    
```
5. Run experiments via the following config. Modify as necessary.
```
    model-analyzer --verbose profile --config-file /config/modelanalyzer.yaml
```

## Notes

To Supply Custom InputData to PerfAnalyzer
- https://github.com/triton-inference-server/server/blob/main/docs/user_guide/perf_analyzer.md#input-data
- https://github.com/triton-inference-server/model_analyzer/issues/529#issuecomment-1249402417
