# DS Playground

# SQL server

We have created a small PostGRES DB containing all the image metadata. 
You can run it dockerized by
```
docker-compose up
docker-compose exec db bash
psql -U remy -d postgres
```

\d
CREATE TABLE users (id SERIAL, name VARCHAR);
INSERT INTO users (name) VALUES ('Alex'), ('Remy');

1. Code structure
1. SQL Querying
1. Computer vision tasks
   1. Geometry (is it a brick, or a set of tiles, or a swatch?)
   1. Color (homogeneity, variance, contrast, saturation)
   1. Texture (veins, dots, lines, grain...?)
1. Given a random image (from a URL, like [this](https://4.bp.blogspot.com/-oyrLdls7rWE/UtVv0Bvt09I/AAAAAAAAAHQ/7BOrneNBaMs/s1600/Bathroom+Designs+2014+1.jpg)), suggest a set of similar materials from the data provided.

### Data

In the following link, you will find a folder containing several images. 

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

You would need to design a distancemodel that takes a random image and returns recommendations. 

### Output
The output should be a runnable python code that we can call from the command line, like:
```bash
$ python recommend.py --url "https://randomsite.com/myimg.jpg"
```
The program should download the image and infer a complementing set of materials. then it should store a JPG file in the `./output` folder with the following naming convention:
```python
f'{surname}_{name}__{time.now()}.jpg'
```
where your name and surname should be inserted.  
This image should have:
*   The original input image
*   Closest 5 products identified by your model
*   Category, provider and material label for each product

You would need to add any jupyter notebooks you might have used to design and train your models. If you used an environment manager like conda or poetry, please add details on how to activate it.

### Bonus
Extra points will be granted for the following:
*   Naming the two closest categories to the input image
*   Find more and cleaner data to work with
*   Explain challenges you encountered and issues likely to arise when working with this kind of images, and how would you solve them.
*   