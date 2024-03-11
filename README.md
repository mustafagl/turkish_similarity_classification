# Türkçe Metin Benzerliği Modeli

Bu notebook, Türkçe metin benzerliği analizi için bir BERT modeli kullanmaktadır. Model, iki cümle arasındaki ilişkiyi belirlemek için eğitilmiştir: çelişki, çıkarım veya nötr.

## Kullanılan Kütüphaneler

- numpy
- pandas
- tensorflow
- transformers

## Veri Seti

Model, [SNLI (Stanford Natural Language Inference)](https://nlp.stanford.edu/projects/snli/) veri setinin Türkçe çevirisini kullanmaktadır. Veri seti, cümle çiftlerinden oluşur ve her çift üç etiketten birine sahiptir: çelişki, çıkarım, nötr.

## Model

Model, `dbmdz/bert-base-turkish-128k-uncased` BERT modelini temel alır ve üzerine iki yönlü LSTM katmanları ve yoğun katmanlar eklenmiştir. Model, veri setindeki etiketlere göre eğitilmiştir.

## Sonuçlar

Model, veri setindeki cümle çiftlerinin ilişkisini başarılı bir şekilde tahmin edebilmektedir. Ancak, modelin performansını daha da artırmak için ek veri setleriyle eğitilmesi ve hiperparametrelerin ayarlanması önerilir.

## Nasıl Kullanılır

Notebook'ta yer alan `check_similarity` fonksiyonu, iki cümlenin benzerliğini kontrol etmek için kullanılabilir. Örnek kullanım:

```python
sentence1 = "İstanbul’da trafik kurallarına uymayan ve agresif tavırlar sergileyen taksiciye arka arkaya 2 ceza kesildi."
sentence2 = "Şehit Eren Bülbül'ün annesi sezonun ilk maçında Trabzonspor stadyumuna geldi"
pred, proba = check_similarity(sentence1, sentence2)
print(f"İlişki: {pred}, Güven: {proba}")
