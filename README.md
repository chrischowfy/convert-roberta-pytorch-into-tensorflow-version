# convert-roberta-pytorch-into-tensorflow-version
My tensorflow enviroment is tensorflow-gpu==1.13,and I use the scripts followed from https://github.com/vickyzayats/roberta_tf_ckpt.
# How to use the script
Step 1:
Download a pytorch version pretrained roberta model and roberta config file from Huggingface's Transformers https://github.com/huggingface/transformers. For convenience, I list the related roberta model links from Huggingface's Transformers:
"roberta-base": "https://cdn.huggingface.co/roberta-base-pytorch_model.bin"

"roberta-large": "https://cdn.huggingface.co/roberta-large-pytorch_model.bin"

"roberta-large-mnli": "https://cdn.huggingface.co/roberta-large-mnli-pytorch_model.bin",
"distilroberta-base": "https://cdn.huggingface.co/distilroberta-base-pytorch_model.bin",
"roberta-base-openai-detector": "https://cdn.huggingface.co/roberta-base-openai-detector-pytorch_model.bin",
"roberta-large-openai-detector": "https://cdn.huggingface.co/roberta-large-openai-detector-pytorch_model.bin",
and the responding config file are :
"roberta-base": "https://s3.amazonaws.com/models.huggingface.co/bert/roberta-base-config.json",
"roberta-large": "https://s3.amazonaws.com/models.huggingface.co/bert/roberta-large-config.json",
"roberta-large-mnli": "https://s3.amazonaws.com/models.huggingface.co/bert/roberta-large-mnli-config.json",
"distilroberta-base": "https://s3.amazonaws.com/models.huggingface.co/bert/distilroberta-base-config.json",
"roberta-base-openai-detector": "https://s3.amazonaws.com/models.huggingface.co/bert/roberta-base-openai-detector-config.json",
 "roberta-large-openai-detector": "https://s3.amazonaws.com/models.huggingface.co/bert/roberta-large-openai-detector-config.json".

Step 2:
Install pytorch_transformers librarys by using "pip install pytorch-transformers" command.
run the "convert_pytorch_checkpoint_to_tf.py" to get a tensorflow version roberta model.
For example, to get the large version roberta, run python3 convert_pytorch_checkpoint_to_tf.py --model_name=roberta-large --config_file=./robert-large-config.json --tf_cache_dir=./output_dir
Step 3:
Since Roberta and Bert have the same model framwork, to use the tensorflow version roberta, you can change a little Bert code:
The tokenization_roberta is from https://github.com/huggingface/transformers/tree/master/src/transformers, put the file at your current path.
tokenizer = tokenization_roberta.RobertaTokenizer.from_pretrained(FLAGS.vocab_file)
the vocab_file is the vocab.json, the model_config_path is the roberta-large-config.json

