## Version : v1.0.0

## Description

**Fields of The World (FTW)** is a comprehensive benchmark dataset designed to enhance the development of machine learning models for instance segmentation of agricultural field boundaries. This dataset aims to meet the growing need for accurate and scalable field boundary data for global agricultural monitoring and assessments.

### Key Features:

1. **Near-Global Coverage**: FTW spans four continents—Europe, Africa, Asia, and South America—covering diverse agricultural landscapes across 24 countries. This extensive geographic coverage allows for the development of models that can generalize well to different agricultural practices and field types.

2. **Large-Scale Dataset**: With approximately 1.6 million parcel boundaries and over 70,000 samples, FTW is significantly larger than previously available datasets. Each sample includes instance and semantic segmentation masks paired with multi-date, multi-spectral Sentinel-2 satellite images, enabling detailed temporal and spectral analysis.

3. **Multi-class Segmentation**: The dataset provides masks for both instance segmentation and semantic segmentation with different classes, including:
   - **Instance Segmentation Masks**: To identify individual fields.
   - **Semantic Segmentation Masks**: 
     - Two-class masks: Background and polygon (field).
     - Three-class masks: Background, polygon (field), and boundaries.

4. **Spectral Richness**: The dataset includes RGB (Red, Green, Blue) and NIR (Near-Infrared) spectral bands from Sentinel-2 images.

5. **Temporal Richness**: The dataset includes multi-date imagery to capture different stages of the growing season. Two images with distinct contrast differences were selected to represent these stages. To determine the date ranges for these images, the USDA Crop Calendar was initially referenced and then refined by selecting periods with minimal cloud cover and optimal contrast between the two images.

6. **Comprehensive Data Splits**: The dataset is carefully divided into training, validation, and test sets to ensure accurate evaluation of model performance. For each country, larger tiles are divided into smaller chips measuring 1536x1536 m². To prevent data leakage due to spatial autocorrelation, a blocked random splitting strategy is used. Chips are grouped into 3×3 blocks, with 80% allocated to training, 10% to validation, and 10% to testing.

7. **Metadata and Documentation**: The metadata and documentation provide crucial information to help users effectively interpret and utilize the dataset. It includes key details about the country of focus, temporal data collection windows, grid structures, and the year of collection.

   1. **Country**: The geographic region the dataset focuses on.
   2. **Crop Types**: Crop types used to filter the polygons in the dataset, with specific keywords used for filtering.
   3. **Seasons**: Date ranges defining the temporal windows for data collection.
   4. **Year of Collection**: The year when the polygon boundaries were captured.
   5. **Grids**: Larger grids from which smaller chips are derived, with some grids spatially separated to optimize area coverage.

---

## Dataset Directory Structure

```
Fields of The World
├── README.md                      -> This File
├── austria                        -> Country Folder
│   ├── label_masks                -> Labels Folder
│   │   ├── instance               -> Instance Segmented Masks (Label) (Masks in .tif Format)
│   │   ├── semantic_2class        -> Semantic Segmented Masks (Label) (Masks in .tif Format) -> Contains 2 Classes (0-Background, 1-Polygon)
│   │   └── semantic_3class        -> Semantic Segmented Masks (Label) (Masks in .tif Format) -> Contains 3 Classes (0-Background, 1-Polygon, 2-Boundaries)
│   ├── s2_images                  -> Images Folder (Contains image chips)
│   │   ├── window_a               -> Window A images (Images in .tif Format)
│   │   └── window_b               -> Window B images (Images in .tif Format)
│   ├── chips_austria.parquet      -> Chips file in geoparquet format, contains split details (Each chips belongs in one of Train/Val/Test split)
│   └── data_config_austria.json   -> Contains meta data about the bigger grids for the dataset, crop types, dates for temporal windows.
├── austria.zip                    -> Country Zip Folder, this contains all the files in the country directory.
└── checksum.md5                   -> Checksum MD5 file containing all the individual files checksum hashes. 
..... Continues for all the countries in the same format.
```

---

## Dataset Information

| Country        | Year of Validity | Parcel Counts | Chips  | Train Split | Validation Split | Test Split | Source Polygons                                                                                 |
| -------------- | ---------------- | ------------- | -----  | ----------- | ---------------- | ---------- | ------------------------------------------------------------------------------------- |
| Austria        | 2021             | 196101        | 6686   | 5304        | 637              | 745        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-austria/description/)     |
| Belgium        | 2021             | 63431         | 1941   | 1554        | 189              | 198        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-belgium/description/)     |
| Brazil         | 2020             | 1854          | 1607   | 1289        | 130              | 188        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-brazil/description/)      |
| Cambodia       | 2021             | 318088        | 344    | 274         | 36               | 34         | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-cambodia/description/)    |
| Corsica        | 2021             | 5360          | 2472   | 1974        | 240              | 258        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-corsica/description/)     |
| Croatia        | 2023             | 157481        | 3482   | 2778        | 351              | 353        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-croatia/description/)     |
| Denmark        | 2021             | 37677         | 3560   | 2868        | 360              | 332        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-denmark/description/)     |
| Estonia        | 2021             | 26695         | 6713   | 5348        | 681              | 684        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-estonia/description/)     |
| Finland        | 2021             | 57323         | 5665   | 4527        | 550              | 588        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-finland/description/)     |
| France         | 2020             | 55342         | 3744   | 2988        | 360              | 396        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-france/description/)      |
| Germany        | 2018/2019        | 4598          | 686    | 306         | 30               | 350        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-germany/description/)     |
| India          | 2016             | 10013         | 2002*  | 1281        | 300              | 399        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-india/description/)       |
| Kenya          | 2022             | 874           | 391    | 316         | 20               | 55         | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-kenya/description/)       |
| Latvia         | 2021             | 44964         | 6938   | 5529        | 668              | 741        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-latvia/description/)      |
| Lithuania      | 2021             | 61424         | 5258   | 4208        | 522              | 528        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-lithuania/description/)   |
| Luxembourg     | 2022             | 29018         | 808    | 643         | 81               | 84         | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-luxembourg/description/)  |
| Netherlands    | 2022             | 43169         | 3879   | 3110        | 381              | 388        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-netherlands/description/) |
| Portugal       | 2021             | 5040          | 86     | 64          | 12               | 10         | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-portugal/description/)    |
| Rwanda         | 2021             | 1532          | 70     | 57          | 6                | 7          | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-rwanda/description/)      |
| Slovakia       | 2021             | 14242         | 4073   | 3275        | 390              | 408        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-slovakia/description/)    |
| Slovenia       | 2021             | 67488         | 2177   | 1733        | 216              | 228        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-slovenia/description/)    |
| South Africa   | 2018             | 6568          | 747    | 590         | 72               | 85         | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-southafrica/description/) |
| Spain          | 2020             | 258465        | 2440   | 2019        | 202              | 219        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-spain/description/)       |
| Sweden         | 2021             | 39718         | 4760   | 3802        | 442              | 516        | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-sweden/description/)      |
| Vietnam        | 2021             | 120913        | 288    | 229         | 36               | 23         | [Link](https://beta.source.coop/repositories/kerner-lab/fields-of-the-world-vietnam/description/)     |

_\*India has a total of 2,002 chips available. Of these, 22 chips are marked as `'none'` for the split column as per the original data curator. Thus, 1,980 chips have been used in the train/validation/test splits in India._
