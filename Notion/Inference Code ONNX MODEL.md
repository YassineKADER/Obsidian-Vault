```Python
import json
import onnxruntime as ort
from pathlib import Path
import shutil
import tempfile
import os

from olive.evaluator.olive_evaluator import OnnxEvaluator
from olive.hardware import AcceleratorSpec
from olive.model import ONNXModel

from whisper_dataset import WhisperDataset

def model_fn(model_dir):
    # SageMaker model loading function
    model_json_path = Path(model_dir) / "model.json"
    with model_json_path.open() as f:
        model_config = json.load(f)

    model = ONNXModel(**model_config["config"])
    session = ort.InferenceSession(str(model_dir / model_config["onnx_file"]))
    
    return {"model": model, "session": session}

def transform_fn(model, input_data, content_type, accept):
    # SageMaker inference function
    dataset = WhisperDataset(data_dir=Path("/opt/ml/processing/input"),  # Adjust the path accordingly
                             use_audio_decoder=model["model"].config["passes"]["prepost"]["config"]["tool_command_args"]["use_audio_decoder"],
                             file_ext=".wav",  # Adjust the file extension accordingly
                             language="haitian",
                             task="transcribe")

    input_data = OnnxEvaluator.format_input(input_data, model["model"].get_io_config())
    output = model["session"].run(None, input_data)

    return output[0][0]

if __name__ == "__main__":
    # Sample data for testing
    audio_path = "./data/tttt.wav"
    output_dir = "./model"  # Adjust the path accordingly

    # Copy the model files to the model directory
    shutil.copytree("path/to/your/onnx/model", os.path.join(output_dir, "model"))
    
    # Save the model configuration to model.json
    model_json_path = Path(output_dir) / "model.json"
    with model_json_path.open("w") as f:
        json.dump({"config": your_model_config}, f)  # Replace 'your_model_config' with the actual model configuration

    # Save the ONNX file to onnx/model.onnx
    onnx_file_path = Path(output_dir) / "onnx" / "model.onnx"
    onnx_file_path.parent.mkdir(parents=True, exist_ok=True)
    shutil.copy("path/to/your/onnx/model.onnx", str(onnx_file_path))

    print("Model files saved to:", output_dir)
```