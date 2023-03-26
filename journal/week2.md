# Week 2 — Distributed Tracing
<h2>Honeycomb</h2>
Honeycomb is a software platform designed for observability and debugging of modern software systems. It provides developers and operations teams with the tools to understand how their applications are behaving in real-time, allowing them to quickly identify and fix issues.
Honeycomb collects data from various sources, including logs, traces, and metrics, and organizes it in a way that makes it easy to search, analyze, and visualize.<br>

<h4> Creating Honeycomb Environment for the Bootcamp </h4>

![1](https://user-images.githubusercontent.com/80603078/226144565-1e39768c-076c-4965-afc0-745cbf62362c.PNG)

<h4> Set environmental variable with the API key of our Honeycomb account: </h4>

```
export HONEYCOMB_API_KEY="aioc00VYJfh1DG6d9BtdcD"<br>
gp env HONEYCOMB_API_KEY="aioc00VYJfh1DG6d9BtdcD"
```


![2](https://user-images.githubusercontent.com/80603078/226145044-b4869bf2-f4a2-41f3-8e38-e79be8641587.PNG)

<h4> Hard code Service Name in Docker compose </h4>

![3](https://user-images.githubusercontent.com/80603078/226145663-d0b2600a-d4aa-4665-acfc-864b14fa41d1.PNG)

<h4> Install packages </h4>


```
opentelemetry-api 
opentelemetry-sdk 
opentelemetry-exporter-otlp-proto-http 
opentelemetry-instrumentation-flask 
opentelemetry-instrumentation-requests

```



![4](https://user-images.githubusercontent.com/80603078/226145818-f40955de-d2fd-4650-b229-6aa0d43a2597.PNG)

<h4> Initializers </h4>

<h5>Add to the app.py :</h5>


```
from opentelemetry import trace
from opentelemetry.instrumentation.flask import FlaskInstrumentor
from opentelemetry.instrumentation.requests import RequestsInstrumentor
from opentelemetry.exporter.otlp.proto.http.trace_exporter import OTLPSpanExporter
from opentelemetry.sdk.trace import TracerProvider
from opentelemetry.sdk.trace.export import BatchSpanProcessor

```


```

# Initialize tracing and an exporter that can send data to Honeycomb
provider = TracerProvider()
processor = BatchSpanProcessor(OTLPSpanExporter())
provider.add_span_processor(processor)
trace.set_tracer_provider(provider)
tracer = trace.get_tracer(__name__)

```

```

# Initialize automatic instrumentation with Flask
app = Flask(__name__)
FlaskInstrumentor().instrument_app(app)
RequestsInstrumentor().instrument()

```

![5](https://user-images.githubusercontent.com/80603078/226182248-40a50723-1ac4-420b-80a3-118a6f9b3db8.PNG)

it shows data :


![6](https://user-images.githubusercontent.com/80603078/226185291-433af485-f051-43d7-b316-9f4a61c648f4.PNG)

<h4> Honeycomb Dashboard is showing Data </h4>

![7](https://user-images.githubusercontent.com/80603078/226185771-cf2d7f56-f173-423c-8a22-0f462de5d8f0.PNG)

![8](https://user-images.githubusercontent.com/80603078/226198494-b1ee6add-2fbb-4e57-aebd-5f2596170e69.PNG)


<h2> Instrument AWS X-Ray : </h2>

Add to the requirements.txt

```
aws-xray-sdk
```
Install python dependencies

```
pip install -r requirements.txt
```

![9](https://user-images.githubusercontent.com/80603078/226208143-d34d7785-c336-4d15-8b2b-c5a88888e8bf.PNG)

### Add to app.py

```py
from aws_xray_sdk.core import xray_recorder
from aws_xray_sdk.ext.flask.middleware import XRayMiddleware
xray_url = os.getenv("AWS_XRAY_URL")
xray_recorder.configure(service='Cruddur', dynamic_naming=xray_url)
XRayMiddleware(app, xray_recorder)
```

![10](https://user-images.githubusercontent.com/80603078/227805151-b15ef107-04be-4de1-bb40-e768b8803fd0.PNG)


### Create group
![11](https://user-images.githubusercontent.com/80603078/227805162-79a04905-b83f-47ac-9797-c782bad243f1.PNG)

###### And it is shown here ! 

![12](https://user-images.githubusercontent.com/80603078/227805170-926b9f95-77a0-40e3-b327-de5ecba64101.PNG)

![13](https://user-images.githubusercontent.com/80603078/227805174-1de204ca-e1cb-4488-9c1b-4a1e85aa21af.PNG)![14](https://user-images.githubusercontent.com/80603078/227805179-7dc8aec1-91f1-4606-b2da-02d5291768e2.PNG)

