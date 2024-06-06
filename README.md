import math

def getPoints():
    points = []
    num_points = int(input("How many points will you enter? "))

    for i in range(num_points):
        x = float(input("{}. enter the x coordinate of the point: ".format(i+1)))
        y = float(input("{}. enter the y coordinate of the point: ".format(i+1)))
        points.append((x, y))

    return points

def euclideanDistance(point1, point2):
    x1, y1 = point1
    x2, y2 = point2
    distance = math.sqrt((x2 - x1) ** 2 + (y2 - y1) ** 2)
    return distance

def calculateDistances(points):
    distances = []
    for i in range(len(points)):
        for j in range(i + 1, len(points)):
            distance = euclideanDistance(points[i], points[j])
            distances.append(distance)
    return distances

def printMinDistance(distances):
    min_distance = min(distances)
    print("Minimum distance:","{:.2f}".format(min_distance))

def main():
    points = getPoints()
    distances = calculateDistances(points)
    printMinDistance(distances)

    if len(points) >= 2:
        distance = euclideanDistance(points[0], points[1])
        print("Distance between first two points:", "{:.2f}".format(distance))
    else:
        print("There are not enough points to calculate distance.")

main()
