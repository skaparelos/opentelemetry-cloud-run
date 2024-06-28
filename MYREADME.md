In collector-config.yaml find this line and replace with the project id:
project_id: xxx # replace with project id

# Usage
use it like:
```
  traceExporter: new OTLPTraceExporter({
    // url: 'http://localhost:4318/v1/traces',

    // we don't need 4318 here because cloud run already is set to that port
    url: 'https://opentelemetry-cloud-run-sample-drfy2etwga-uc.a.run.app/v1/traces', 
    headers: {}
  }),
```

# deploy as a cloud run service
gcloud beta builds submit . --config=cloudbuild.yaml

# run locally
docker build -t otel-collector .
docker run -p 4318:4318 otel-collector

