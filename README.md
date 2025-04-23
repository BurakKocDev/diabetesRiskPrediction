# diabetesRiskPrediction
1. Kütüphanelerin İçe Aktarılması
Kodun başında veri analizi, görselleştirme ve makine öğrenmesi modelleri için gerekli olan tüm kütüphaneler içe aktarılmıştır:

pandas, numpy: Veri işleme ve analiz.

matplotlib, seaborn: Görselleştirme.

sklearn: Modelleme, ölçekleme, model değerlendirme ve hiperparametre optimizasyonu.

warnings: Uyarıları bastırmak için.

2. Veri Yükleme ve Ön Analiz
diabetes.csv dosyası pandas ile yüklenmiştir.

df.info() komutu ile veri setinin sütun bilgileri, veri tipleri ve eksik veriler kontrol edilmiştir.

df.describe() ile istatistiksel özet alınmıştır.

3. Görselleştirme
sns.pairplot ile Outcome değişkenine göre dağılım görselleştirilmiştir.

Özellikler arası korelasyon heatmap ile gösterilmiş ve en yüksek ilişkiler analiz edilmiştir.

4. Aykırı Değer Tespiti ve Temizleme
IQR yöntemi ile aykırı değerler detect_outliers_iqr() fonksiyonu ile tespit edilmiştir.

Belirlenen aykırı veriler çıkarılarak yeni bir temiz veri seti (df_cleaned) oluşturulmuştur.

5. Veri Bölme ve Ölçekleme
Hedef değişken Outcome ayrılarak veri X (özellikler) ve y (etiketler) şeklinde ayrılmıştır.

Veriler %75 eğitim ve %25 test olarak bölünmüştür.

StandardScaler kullanılarak veriler standartlaştırılmıştır.

6. Temel Modellerin Eğitimi ve Değerlendirmesi
Aşağıdaki modeller 10-fold cross-validation ile test edilmiştir:

Logistic Regression

Decision Tree

K-Nearest Neighbors

Gaussian Naive Bayes

Support Vector Machine

AdaBoost

Gradient Boosting

Random Forest

Her modelin doğruluk ortalaması ve standart sapması yazdırılmıştır. Sonuçlar boxplot ile görselleştirilmiştir.

7. Karar Ağacı Modeli için Hiperparametre Optimizasyonu
GridSearchCV ile Karar Ağacı için hiperparametreler test edilmiştir:

criterion: gini veya entropy

max_depth: 10–50 arası

min_samples_split: 2, 5, 10

min_samples_leaf: 1, 2, 4

En iyi parametreler:

python
Kopyala
Düzenle
{'criterion': 'gini', 'max_depth': X, 'min_samples_split': Y, 'min_samples_leaf': Z}
(Not: Çıktıda belirli değerler gözükmemekte. Gerçek çıktı çalıştırıldığında görülür.)

8. Modelin Test Edilmesi
Test verisi üzerinden tahmin yapılarak model performansı ölçülmüştür.

Confusion Matrix:

lua
Kopyala
Düzenle
[[88 21]
 [28 23]]
Bu sonuçlara göre:

88 doğru negatif

23 doğru pozitif

28 yanlış negatif

21 yanlış pozitif

Classification Report çıktı:

Precision, Recall, F1-score ve Accuracy gibi metrikler özetlenmiştir.

9. Yeni Veri Üzerinde Tahmin
Yeni bir hasta verisi üzerinden tahmin yapılmıştır:

python
Kopyala
Düzenle
new_data = np.array([[6,149,72,35,0,34.6,0.627,51]])
Model sonucu: Pozitif/Negatif (0 veya 1 olarak çıktı verir)

✅ Sonuç ve Öneriler
Karar Ağacı modeli, hiperparametre optimizasyonu ile geliştirilmiş ve iyi bir doğruluk oranı yakalanmıştır.

Aykırı değerlerin çıkarılması model performansını iyileştirmiştir.

Daha fazla veri ve farklı model kombinasyonları denenerek sonuçlar geliştirilebilir.

Modelin recall ve precision skorları yakından incelenerek sağlık açısından kritik olan yanlış negatiflerin azaltılmasına odaklanılabilir.

*********************************
1. Importing Libraries
The following libraries were imported for data processing, visualization, and machine learning:

pandas, numpy: Data handling and analysis.

matplotlib, seaborn: Visualization.

sklearn: For preprocessing, modeling, evaluation, and hyperparameter tuning.

warnings: To suppress warnings.

2. Data Loading and Initial Analysis
The dataset diabetes.csv was loaded using pandas.

df.info() was used to check column names, data types, and missing values.

Descriptive statistics were obtained using df.describe().

3. Visualization
A pairplot was generated using seaborn to visually inspect feature distributions based on the Outcome.

A correlation heatmap was plotted to identify relationships between features.

4. Outlier Detection and Cleaning
Outliers were detected using the IQR method via the detect_outliers_iqr() function.

The identified outliers were removed, and a cleaned dataset (df_cleaned) was created.

5. Data Splitting and Scaling
The feature set X and target y (Outcome) were separated.

Data was split into 75% training and 25% testing sets.

Standardization was applied using StandardScaler.

6. Baseline Model Training and Evaluation
Eight machine learning models were tested using 10-fold cross-validation:

Logistic Regression

Decision Tree

K-Nearest Neighbors

Gaussian Naive Bayes

Support Vector Machine

AdaBoost

Gradient Boosting

Random Forest

The mean accuracy and standard deviation for each model were printed, and performance was visualized using a boxplot.

7. Hyperparameter Tuning for Decision Tree
GridSearchCV was used to search for the best hyperparameters:

criterion: gini or entropy

max_depth: range from 10 to 50

min_samples_split: 2, 5, 10

min_samples_leaf: 1, 2, 4

The best parameters found:

python
Kopyala
Düzenle
{'criterion': 'gini', 'max_depth': X, 'min_samples_split': Y, 'min_samples_leaf': Z}
(Actual values appear when the code is run.)

8. Model Testing on Test Data
The tuned decision tree model was tested on the test set.

Confusion Matrix:

lua
Kopyala
Düzenle
[[88 21]
 [28 23]]
Which means:

88 true negatives

23 true positives

28 false negatives

21 false positives

Classification Report included:

Precision, Recall, F1-score, and Accuracy

9. Prediction on New Data
The model was tested on a new patient record:

python
Kopyala
Düzenle
new_data = np.array([[6,149,72,35,0,34.6,0.627,51]])
The model returned a prediction: Positive/Negative (1 or 0)

✅ Conclusion and Recommendations
Decision Tree classifier was successfully tuned and achieved good accuracy.

Removing outliers improved overall performance.

Further improvements could be made by:

Trying other model types or ensemble methods

Balancing the dataset

Focusing on reducing false negatives due to the health impact
 
