# Explanation available as [PDF](https://github.com/samyak-jain/mbrdiSubmission/blob/master/MercedesHack.pdf)
# Pseudocode

```python
opendrive = read_xml("data.xodr")
vehicle_data = opendrive["vehicleposition"]
json_data = toJson(opendrive)
json_data = json_data.concat(measurements_from_sketchup)
roads = json_data["roads"]
data = json_data["coordinates"]

# Shadow calculation
'''
 Calculate the lenght of shadow based on height of object and angle of light source
 Agrs
 height: height of object
 theta: angle to light source
 Return
 length: length of shadow
'''
def shadow_calculator(height, theta):
 length = h*cot(theta)
 return length

shadow = shadow_calcualtor(data["height"], data["alpha"])


# Numpy sampling
'''
 Sampling the number of points in the lidar cloud space
 Calculating the Field Of View (FOV)
 Args
 height: elevation of LIDAR
 separation: degree of separation
 channels: number of channels
 theta: mount angle
 Return
 upper: upper limit of FOV
 lower: lower limit of FOV
'''
def fov(height, separation, channels, theta):
 lower = height*tan(theta)
 alpha = theta + channels*separation
 upper = height*tan(alpha)
 return upper, lower

up, low = fov(data["height"], data["separation"], data["channels"], data["theta"])


# Calculation
'''
 Calculate the lidar point cloud
 Args
 upper: upper limit of FOV
 lower: lower limit of FOV
 sepatation: degree of separation
 Return
 cloud: lidar point cloud matrix
'''
def point_cloud(upper, lower, separation):
 from lower to upper through separation:
  points = [number of points per channel]
  for point in points:
   x, y, z coordinates
   Calculate height and alpha
   shadow = shadow_calcualtor(height, alpha)
   if shadow:
    point value 0
   else:
    point value 1
  cloud.append((x, y, z, point value)
 return cloud

cloud = point_cloud(up,low, 0.625)

# Object detection
objects = vote3deep(cloud)
```
