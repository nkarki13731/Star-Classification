1. Context Of the Problem
If we gaze in our night sky, we can observe numerous stars twinkling in the sky. Although they
look similar, they significantly differ in terms of stellar properƟes such as temperature, stellar
mass, luminosity, radius, color, etc. These differences are categorized using spectral types: O,
B, A, F, G, K, and M. This classificaƟon based on observable features can help astrophysicists
uncover stellar formaƟon paƩerns and galaxy structures. For an instance O-type stars, live
only a few million years before exploding as supernovae, whereas smaller, cooler stars (such
as K or M types) can shine for billions of years. So,knowing a star’s spectral type reveals its
stage in the stellar life cycle. Also, idenƟfying these types in galaxies pinpoints regions of
recent star birth (marked by short-lived O and B stars) and disƟnguishes older stellar
populaƟons. On the other hand, the spectral classificaƟon system is a powerful educaƟonal
tool. It offers a clear way to illustrate the diversity of stars and their life cycles to anyone who
is fascinated with universe and stars, they can enrich their knowledge by understanding these
spectral types and how they differ.
As a result, the OBAFGKM classificaƟon not only aids astronomers in studying stars and
galaxies but also helps enthusiasts and even students understand the huge range of stars in
the universe.
So, in this Project I am classifying Stars into their spectral Types with the help of their stellar
properƟes.
Dataset DescripƟon
For this project, I am using Gaia DR3 version 2 dataset from Kaggle. The dataset was uploaded
by the user RealKiller69. In this dataset, there are 626,000 different observaƟons(stars)
divided into 100k instances for each spectral class: B, A, F, G, K, M and 26016 for O type stars
with and 50 different features per observaƟon which gives 50 unique properƟes of a star.
The key features I am using for this project from the dataset are:-
1. Teff:- The star’s effecƟve temperature in Kelvins, indicaƟng how hot the It is Key for
disƟnguishing hoƩer spectral types (e.g., O, B) from cooler types
2. Rad:- The star’s esƟmated radius in units of solar radii. It Helps classify whether the star is
larger (giant/supergiant) or smaller (dwarf), linking size to luminosity.
3. Gmag:- Apparent magnitude in Gaia’s G band, a measure of the star’s brightness as seen
from Earth. It used with distance to esƟmate absolute brightness; also supports
classificaƟon since brighter/hoƩer stars tend to have smaller (more negaƟve) magnitudes.
4. BPmag:- Apparent magnitude in Gaia’s BP (blue) band.It is the brightness at shorter
(bluer) wavelengths, important for idenƟfying hoƩer, bluer stars.
5. RPmag:- Apparent magnitude in Gaia’s RP (red) band. It is the Brightness at longer
(redder) wavelengths, helping differenƟate cooler stars.
6. GMAG:- Absolute G magnitude; how bright the star would appear if placed at a standard
distance (10 parsecs).Used to Reflects intrinsic brightness, free from distance effects—
crucial for comparing stellar luminosiƟes directly.
7. E(BP-RP) :-Color excess between BP and RP magnitudes, indicaƟng how dust may redden
a star’s observed color. A higher value suggests more interstellar dust or reddening,
important for correcƟng colors and magnitudes.
8. Logg:-The log (base 10) of the star’s surface gravity (g). Helps disƟnguish giants (low logg)
from dwarfs (high logg); also Ɵed to a star’s mass and evoluƟon stage.
9. [Fe/H]:- A measurement of the star’s metallicity, i.e., the raƟo of iron to hydrogen relaƟve
to the Sun.Metallicity can influence star formaƟon history and spectral classificaƟon
details.
10. Plx:- Trigonometric parallax in milliarcseconds. Inversely related to distance; a
fundamental measurement for deriving stellar distances.
11. PM:- Total proper moƟon in milliarcseconds per year, combining moƟon in right ascension
and declinaƟon. IdenƟfies how fast a star moves across the sky.
12. Dist:- EsƟmated distance to the star in parsecs (oŌen from 1/parallax).
13. ABP:- ExƟncƟon in the BP band. QuanƟfies how much dust dims the BP flux, helping
correct apparent magnitudes.
14. ARP:-ExƟncƟon in the RP band. Similar to ABP, but at redder wavelengths; used for dust
correcƟons in the RP band.
I couldn’t use some of the features from the dataset which I wanted to use such as Mass-Flame,
Age-Flame , evoluƟon stage ,etc. Because when filtered these features significantly dropped
count of some of the classes which I will talk in brief in next part of the report. Also some of the
features like evoluƟon stage were numerical encoded with no informaƟon of encoding in the site
where I got dataset from nor in the Gaia’s catalogue which was fascinaƟng.
Data preprocessing EDA and findings:-
To analyze the Gaia dataset, I followed a step-by-step process to clean, prepare, and explore the
data in a meaningful way. First, I loaded the dataset, which had over 626,000 rows and 50
columns, with 100k instances of each spectal type except fot O-type stars. I then explored the
data by checking the structure, types of values, and the presence of any missing data. My dataset
had informaƟon such as star posiƟons, brightness, temperature, size, type and other stellar
properƟes.

Next, I focused on cleaning the data. I removed any rows that had missing values in important
columns such as luminosity (Lum-Flame), radius (Rad), and temperature (Teff). I also divided the
stars into groups based on their spectral type: O, B, A, F, G, K, and M stars. This helped me study
each group separately.Because some values were very large and varied a lot, I used log
transformaƟon on key features like temperature, radius, and luminosity. This made it easier to
compare values and create beƩer visualizaƟons. I also removed extreme outliers using the Z-score
method, which idenƟfies values that are very far from the average. This helped make the data
more accurate and reliable.
Once the data was clean, I combined all the star groups into one dataset with a new column called
“Class” to label the type of star. Then I used visual tools like violin plots, histograms, scaƩer plots,
and heatmaps to explore and compare features like luminosity, radius, and temperature between
star types. These plots helped me understand how O-type stars are much brighter, hoƩer and
more luminous followed by B , A, F,G,K and M. Also posiƟve correlaƟon between radius and
luminosity is found for the stars. For some stars like M stars and K stars it was also observed that
they had stars with stars with small and larger radius hinƟng presence of subclass within them.
Then I moved on to see the the observed brightness vs actual brightness of these stars. For this I
looked at apparent(Gmag) and absolute magnitude(GMAG) of these stars. In my dataset the
brightness of stars is measured using different types of magnitudes based on light captured
through different filters, I chose Gmag as my apparent magnitude since it was highly correlated
with RPmag and BPmag.As a result I found out that O-type stars are the brightest because they
have the lowest absolute magnitude. M-type stars are less bright overall, even if some of them
look bright from Earth because they are closer.
Then I did some feature engineering, I created two new features BP-RP and BP-RP0. Where BPRP tells us about the color index of a star, smaller values usually mean the star is hoƩer and bluer,
while larger values mean it’s cooler and redder whereas BP-RP0 is s the corrected color index. I
subtracted E(BP-RP), which is the exƟncƟon or reddening caused by dust, from BP-RP to get a
cleaner value. This helps show the star’s true color without the effect of interstellar dust between
us and the star. I also used Gaia’s exƟncƟon values where ABP and ARP represent how much blue
and red light, respecƟvely, are dimmed by interstellar dust, and I created a new feature ABP - ARP
to measure the difference in exƟncƟon between blue and red light, helping to understand the
amount of reddening each star experiences due to dust. Then I analyzed how these color values
change across star types, I found that the corrected color index BP-RP0 increases from O-type to
M-type stars, which reflects the change from hot, blue stars to cool, red stars. This shows how
star color is closely related to temperature. I also noƟced that the ABP - ARP values vary between
different types of stars. O-type and M-type stars showed more variaƟon in reddening, which
means they are more affected by interstellar dust, while other star types are less affected.
Finally, I applied another round of outlier removal on important features like surface gravity(log
g), temperature, parallax, metallicity etc. .using Z-score filtering and carried out more analysis.
This gave me a final clean dataset that’s ready for my modeling.
In summary, this approach involved cleaning the data, transforming it for beƩer comparison,
removing outliers, and using clear visualizaƟons to compare different types of stars. It helped
highlight key differences between star classes and prepared the dataset for future modeling tasks.
Modeling Approach and Findings
AŌer preparing and engineering features, I selected a refined set of features for my classificaƟon
modeling.Before training my model, I used PCA and UMAP to reduce the data to 2D and see how
well the star types are separated. In the PCA plot, some star classes like M-stars and O-stars are
clearly grouped, but F-stars, G-stars, and K-stars overlap a lot, meaning the model might confuse
them ,however umap had too much overlapping between many classes, making it hard to tell
them apart.AŌer that Redundant and highly correlated features were dropped to avoid
mulƟcollinearity, guided by correlaƟon heatmaps. Standard scaling was applied before training
models. I used mulƟple classificaƟon models, including LogisƟc Regression, Random Forest, and
XGBoost as my base models. All of my models did very well with 87% model and cross validaƟon
accuracy for logisƟc regression and accuracy ,cross validaƟon accuracy and F1 score of almost
90% for the Random Forest classifier and XGBoost , suggesƟng that the models were performing
good with no overfiƫng and maintaining good raƟo between Recall and Precision. But in all of
the three models there was something common, F1 score for two classes i.e. F-Stars and G-stars
were significantly lower than compared to any other classes i.e. 78% for F-stars and 74 % for Gstars . Confusion matrices showed these two classes were oŌen mistaken for one another. I tried
different methods to fix this issue, including oversampling the underforming classes with SMOTE
and tuning model parameters, but no promising results were found.
Then To understand where my model was making mistakes between F-stars and G-stars, I created
KDE (kernel density esƟmate) plots comparing the distribuƟons of different features for correctly
and incorrectly predicted stars. These plots show how certain features like temperature
(Teff_log), color index (BP-RP0), luminosity (Lum-Flame-Log), gravity (logg), and radius (Rad-log)
are distributed for both correct and incorrect predicƟons.
By looking at these plots, I could see that in many cases, the distribuƟons of correct and incorrect
predicƟons overlapped heavily, especially for features like temperature and color index. This
suggests that the model struggles to tell F-stars and G-stars apart not because of random noise,
but because they have very similar values for these features. The overlapping shapes in the plots
helped confirm that the misclassificaƟons are due to feature similarity rather than poor data
quality. To support this claim I even performed regression modeling using only those two
underperforming classes. The goal was to check if the predicƟon errors were due to noise in the
data (random variaƟon) or due to the overlap of physical features between these two types of
stars. I trained models like linear regression, ridge regression, random forest, and XGBoost to
predict the temperature (Teff_log) using features like color index, luminosity, radius, gravity, and
metallicity. The models showed very high R² scores, meaning the features were strongly related
to the target. This suggested that the features were not noisy, but rather very similar between F
and G stars.
Finally , to evaluate how well the model disƟnguishes F-stars and G-stars, I ploƩed Precision-Recall
(PR) curves for both classes. These curves help visualize the balance between precision and recall
at different probability thresholds.For F-stars, the model achieved an Average Precision (AP) score
of 0.888, showing high overall performance. Precision remains high even as recall increases,
meaning the model can correctly idenƟfy most F-stars without making too many false
predicƟons.For G-stars, the AP score was slightly lower at 0.819, suggesƟng that the model has a
bit more difficulty disƟnguishing G-stars, likely due to their overlap in feature space with other
classes (especially F-stars). The precision for G-stars drops more noƟceably as recall increases,
meaning that when the model tries to catch more G-stars, it also includes more incorrect ones.
Overall, among precision, recall, and F1 score, the F1 score was the most important metric in this
project, as it balances both correctness and completeness of the model’s predicƟons. Since some
star types, like F and G stars, have overlapping features, and changing classificaƟon thresholds
affects this balance, using F1 score provided the most reliable measure of overall model
performance. In addiƟon, adjusƟng the classificaƟon threshold is a useful way to tune precision
and recall depending on the needs of future projects. For example, lowering the threshold
increases recall by idenƟfying more true cases, while raising it increases precision by reducing
false posiƟves. This flexibility allows future models to be tailored based on whether it's more
important to find all possible stars of a type or to make fewer, more confident predicƟons.
Future Steps
In future work, I plan to invesƟgate addiƟonal features such as parallax (Plx) and proper moƟon
(PM) to explore the moƟon of stars in more depth. These features can help determine whether
stars are moving significantly, which could reveal insights about their distance, presence in binary
systems or neutron stars. I also aim to experiment with threshold tuning more intenƟonally,
adjusƟng it based on project goals for example, increasing recall to detect more stars or boosƟng
precision for higher predicƟon confidence. This flexibility will be especially useful in tailoring
models to different scienƟfic needs or observaƟonal prioriƟes.
References
hƩps://www.perkins.org/resource/apparent-vs-absolute-magnitude-stars-interacƟvemodel/#:~:text=absolute%20magnitude%20%E2%80%93%20a%20measure%20of,star%20as%2
0seen%20from%20Earth
hƩps://lweb.cfa.harvard.edu/~pberlind/atlas/htmls/note.html
hƩps://astrobackyard.com/types-of-stars/
hƩps://www.astronomy.com/astronomy-for-beginners/why-is-a-parsec-3-26-light-years/
hƩps://web.njit.edu/~gary/202/Lecture16.html
