# Local Voice Assistant (Yerel Sesli Asistan)

Bu proje, yerel olarak (internet bağlantısı olmadan) çalışan, kişiselleştirilebilir bir sesli asistandır. Kullanıcının sesli komutlarını anlar, yerel bir dil modeli ile cevaplar üretir ve bu cevapları klonlanmış bir sesle kullanıcıya geri okur.

## 🚀 Kullandığı Teknolojiler

Bu asistan, üç temel yapay zeka modelinin birleşiminden oluşur:

* **🎙️ Speech-to-Text (Sesi Metne Çevirme): [OpenAI Whisper](https://github.com/openai/whisper)**
    * Kullanıcının mikrofonundan gelen sesi yüksek doğrulukla metne dönüştürür. Projede `base` modeli kullanılmıştır ve Türkçe diline ayarlanmıştır.

* **🧠 Large Language Model (Büyük Dil Modeli): [Ollama](https://ollama.com/)**
    * Metne dönüştürülen komutlara akıllı cevaplar üretir. Proje, `llama3.1` veya `phi3:mini` gibi yerel olarak çalıştırılabilen modellerle uyumludur.

* **🗣️ Text-to-Speech (Metni Sese Çevirme): [Coqui TTS](https://github.com/coqui-ai/TTS)**
    * Ollama'nın ürettiği metin cevaplarını, sağlanan referans bir ses dosyasını (`hedef_ses.wav`) kullanarak klonlanmış bir sesle seslendirir. Projede `xtts_v2` modeli kullanılmıştır.

## 🛠️ Kurulum ve Çalıştırma

1.  **Depoyu Klonlayın:**
    ```bash
    git clone [https://github.com/AhmetEren79/local-voice-assistant.git](https://github.com/AhmetEren79/local-voice-assistant.git)
    cd local-voice-assistant
    ```

2.  **Gerekli Paketleri Yükleyin:**
    * Projeyi çalıştırmak için [Ollama](https://ollama.com/)'yı sisteminize kurun.
    * Bir dil modeli indirin (örneğin `ollama pull llama3.1`).
    * Python sanal ortamını oluşturun ve bağımlılıkları yükleyin:
    ```bash
    python -m venv venv
    venv\Scripts\activate  # Windows için
    pip install -r requirements.txt
    ```

3.  **Asistanı Çalıştırın:**
    * Bir terminalde Ollama modelini çalışır durumda bırakın: `ollama run llama3.1`
    * `asistan.py` dosyasını çalıştırın: `python "Ses Asistan/asistan.py"`
    * Konuşmak için **Boşluk (space)** tuşuna basın.

## ⚙️ Yapılandırma

* **Model Seçimi:** `asistan.py` dosyasının en üstündeki `KULLANILACAK_MODEL` değişkenini değiştirerek farklı Ollama modelleri arasında geçiş yapabilirsiniz.
* **Ses Klonlama:** Asistanın konuşacağı sesi değiştirmek için `Ses Asistan` klasörünün içindeki `hedef_ses.wav` dosyasını kendi ses dosyanızla değiştirin.
