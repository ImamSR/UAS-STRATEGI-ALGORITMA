# UAS-STRATEGI-ALGORITMA
Untuk Memenuhi SOAL UAS NO 3
```py
distances = [10, 25, 30, 40, 50, 75, 80, 110, 130]
rest_interval = 30
total_distance = 140

def brute_force(distances, rest_interval, total_distance):
    n = len(distances)
    min_stops = n  
    best_combination = None

    for i in range(2**n):
        combination = bin(i)[2:].zfill(n)
        stops = combination.count('1')

        if stops > 0 and calculate_distance(combination, distances, rest_interval) == total_distance:
            if stops < min_stops:
                min_stops = stops
                best_combination = combination

    return min_stops, best_combination

def calculate_distance(combination, distances, rest_interval):
    stops = [i for i, stop in enumerate(combination) if stop == '1']
    stops_distances = [distances[i] for i in stops]
    distances_between_stops = [stops_distances[i] - stops_distances[i-1] for i in range(1, len(stops_distances))]
    total_distance = sum(distances_between_stops) + (len(stops) - 1) * rest_interval
    return total_distance

min_stops, best_combination = brute_force(distances, rest_interval, total_distance)

print("Jumlah perhentian terkecil yang dibutuhkan:", min_stops)
print("Kombinasi perhentian terbaik:", best_combination)
```
