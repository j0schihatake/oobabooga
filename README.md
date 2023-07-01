# oobabooga
tests

youtobe:  https://www.youtube.com/watch?v=cCQdzqAHcFk

web ui:  https://github.com/oobabooga/text-generation-webui

docker:  https://github.com/Atinoda/text-generation-webui-docker

git lfs install
git clone https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g      модель викуны

Ссылка на репозиторий с перечислением моделей:  https://github.com/underlines/awesome-marketing-datascience/blob/master/awesome-ai.md




Преобразование весов: https://huggingface.co/docs/transformers/main/en/model_doc/llama

Кажется, работает и со StableVicuna https://stability.ai/blog/stablevicuna-open-source-rlhf-chatbot

Вот шаги, если кто-то сочтет это полезным:

git clone https://huggingface.co/CarperAI/stable-vicuna-13b-delta 
cdстабильный-vicuna-13b-delta 
pip install torch tqdm transformers sentencepiece 
python3 apply_delta.py --путь к базовой модели <путь к весам ламы в формате transformers> --путь к целевой модели стабильный-vicuna-13b --delta-path .
cd llama.cpp
python convert-pth-to-ggml.py ./models/stable-vicuna-13b 1
./quantize ./models/stable-vicuna-13b/ggml-model-f16.bin ./my-models/stable-vicuna-13b/ggml-model-q4_0.bin q4_0
Чтобы преобразовать веса ламы в формат transformers, я использовал это руководство

git clone git@github.com:huggingface/transformers.git 
трансформеры на CD 
pip install accelerate protobuf==3.20 sentencepiece tokenizers 
python src/transformers/models/llama/convert_llama_weights_to_hf.py --input_dir <путь к весам ламы> --model_size 13B --output_dir <путь к весам ламы в формате transformers>
(для этого требуется ~ 30 ГБ оперативной памяти)
