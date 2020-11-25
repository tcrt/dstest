Distance Test
===


1. Code structure
1. SQL Querying
1. Computer vision tasks

1. Given a random image (from a URL, like [this](https://4.bp.blogspot.com/-oyrLdls7rWE/UtVv0Bvt09I/AAAAAAAAAHQ/7BOrneNBaMs/s1600/Bathroom+Designs+2014+1.jpg)), suggest a set of similar materials from the data provided.

### Data

The [starting dataset](link) is a collection of images coming out of a generalist search engine. We have collated some metadata in the [accompanying csv](./assets/2011_material_info.csv), which has the following columns:

| Column | Description |
| ------ | ----------- |
| `category` | The category we searched for in the search engine |
| `dimension_a` | A random dimension |
| `dimension_b` | A random dimension |
| `finishing` | A random finishing |
| `img_info_percentage` | Percentage of the image that contains information |
| `main_color` | Main RGB triplet  |
| `main_color_frequency` | Percentage of the image containing the main color |
| `material` | A randomized material |
| `palette` | Set of predominant 5 colors in the image |
| `price` | A random price |
| `provider` | A random provider |
| `uuid` | Unique identifier |
| `weight` | A random weight |


Each one of the images pertains to one of the following categories: 

```
category             count
--------------------------
sofa                  1510
natural stone tile     911
bathroom tiles         896
kitchen tile           885
ceramic tile           867
azulejo portugues      600
wood tile              593
```

Beware that the provided dataset is not real data, but images taken from search engines - inconsistencies are to be expected.  

You would need to design a distance model that takes a random image and returns the closest 5 recommendations.

### Output
The output should be a runnable python code that we can call from the command line, like:
```bash
$ python recommend.py --url "https://randomsite.com/myimg.jpg"
```
The program should download the image and infer a complementing set of materials. Then it should store a JPG file in the `./output` folder with the following naming convention:
```python
f'{surname}_{name}__{time.now()}.jpg'
```
where your name and surname should be inserted.  
This image should have:
*   The original input image
*   Up to 8 of the closest products identified by your model
*   Category, provider and material label for each product

![dsitances](./assets/distance01.jpg)

Distance algorithms tend to be biased on colour. Can you propose a way to alleviate this, so the model can return similar images attending to other structural properties of the image like
*   Geometry (is it a brick, or a set of tiles, or a swatch?)
*   Color homogeneity, variance, contrast, saturation...
*   Texture (veins, dots, lines, grain...)

Extra points if you come up with a model that can take these into account on user input - you might need to enrich the dataset first. 

### Bonus
Extra points will be granted for the following:
*   Naming the two closest categories to the input image
*   Explain how you would find more and cleaner data to work with
*   Explain potential enrichment processes that could improve the distance algorithm
*   Explain challenges you encountered and issues likely to arise when working with this kind of images, and how would you solve them. Special emphasis on issues of scale, lighting, distortion, etc.
*   Knowledge and application of Image augmentation techniques

***
You would need to add any jupyter notebooks you might have used to design and train your models. Well documented code is a plus. If you used an environment manager like conda or poetry, please add details on how to activate it.