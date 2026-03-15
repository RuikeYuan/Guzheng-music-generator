# Chinese Guzheng Music Tool

## 1. Project Aims

This project aims to develop an AI-generated traditional Chinese music tool, specifically focusing on the Guzheng, a classic Chinese musical instrument. Currently, most AI music generation models mainly produce western music styles — tools that can generate music perfectly in the style of traditional Chinese instruments are rare. Our goal is to fine-tune a generative music model so that it learns the unique characteristics of Guzheng music and creates new compositions in this style. By doing so, the tool can assist users, including those unfamiliar with Guzheng composition, by providing AI-generated music that captures the essence of this instrument.

---

## 2. Background Research

Existing generative music tools, like Meta's MusicGen, focus mainly on western genres (pop, jazz, classical). Google's Magenta also offers music generation functions but does not support traditional Chinese music well. Our tool is based on Meta’s MusicGen, intending to train the model using Guzheng performance recordings. We preprocess real Guzheng performances with audio techniques like pitch shifting and time stretching to augment the dataset. Our research also references AI-assisted music generation studies and symbolic representation techniques (e.g., MIDI conversion) to enhance the model's structured composition capability.

---

## 3. Implementation

- **Data Collection:** We gathered Guzheng recordings from sources such as YouTube.
- **Preprocessing:** Audio files were converted from MP3 to WAV, trimmed, and augmented (pitch shifting, time stretching).
- **Dataset Preparation:** Files were transformed into a suitable format for model training.
- **Model Training:** The intended workflow was to fine-tune MusicGen in a Colab environment with GPU acceleration.
- **Music Generation:** After training, the model would generate new Guzheng-style music saved as WAV files.

However, during implementation, we discovered MusicGen does not currently support personalized fine-tuning or training. It can only generate music via prompts, allowing adjustment of only music length and model size (small/medium/large), not training with custom data. We then attempted to use Google’s Magenta, which supports style-continuation inference—generating music that extends from an input sample in a similar style. This approach encountered major compatibility and dependency conflicts (TensorFlow, fsspec, basic-pitch, Magenta), preventing successful import and usage of core modules.

---

## 4. Example Outputs

The generated Guzheng music files, `guzheng_music.wav` and `guzheng_music_1.wav`, are available on Brightspace. These files were produced using MusicGen with various prompts and model sizes, but are not based directly on the processed Guzheng dataset. This demonstrates the limitation: without specific fine-tuning, the output cannot fully reflect unique Guzheng musical characteristics.

---

## 5. Reflection and Future Work

While the project provides a practical tool for musicians and researchers interested in Guzheng compositions, it does not fully achieve the original goal. The AI-generated music captures some Guzheng qualities but is not perfect. The major limitation was the inability to fine-tune MusicGen; resolving Magenta's compatibility issues is our priority for next steps. If MusicGen eventually supports fine-tuning, that would greatly improve the tool.

Additionally, the limited dataset may not fully represent all Guzheng characteristics and melodic patterns. Fine-tuning also requires significant computational resources. Future work should focus on:
- Expanding the Guzheng dataset with more performances
- Improving model training processes to better capture stylistic details
- Developing an interactive web interface for Guzheng music generation and customization.

---

## Usage

You can use the current MusicGen model to generate Guzheng-style music by providing descriptive prompts and adjusting model parameters. For example:

```python
from musicgen import generate

output = generate(prompt="Chinese Guzheng traditional style", length=30, model_size='medium')
```

> *Note: Fine-tuning with custom data is not currently supported as of March 2026.*

---

## License

This project is for academic/research purposes only.
