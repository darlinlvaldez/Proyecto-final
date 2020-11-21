Pattern: Sliding Window.
Dada una lista de numeros positivos y un numero positivo "k", encuentre la suma maxima de cualquier submatriz contigua de tamaño "k".

Input: [2, 1, 5, 1, 3, 2], k=3

Output: 9

def max_sub_array_of_size_k(k, arr):
  max_sum , window_sum = 0, 0
  window_start = 0

  for window_end in range(len(arr)):
    window_sum += arr[window_end] 

    if window_end >= k-1:
      max_sum = max(max_sum, window_sum)
      window_sum -= arr[window_start]
      window_start += 1
  return max_sum


def main():
  print("Maximum sum of a subarray of size K: " + str(max_sub_array_of_size_k(3, [2, 1, 5, 1, 3, 2])))
  print("Maximum sum of a subarray of size K: " + str(max_sub_array_of_size_k(2, [2, 3, 4, 1, 5])))

main()





Pattern: Two pointers.

Dada una lista de numeros ordenados, elimine todos los duplicados. No debe utilizar ningun espacio adicional; despues de eliminar los duplicados en el lugar, devuelva la longitud del subarreglo que no tiene duplicado.

Input: [2, 3, 3, 3, 6, 9, 9,]

Output: 4


def remove_duplicates(arr):

  next_non_duplicate = 1

  i = 1
  while(i < len(arr)):
    if arr[next_non_duplicate - 1] != arr[i]:
      arr[next_non_duplicate] = arr[i]
      next_non_duplicate += 1
    i += 1

  return next_non_duplicate


def main():
  print(remove_duplicates([2, 3, 3, 3, 6, 9, 9]))
  print(remove_duplicates([2, 2, 2, 11]))

main()






Pattern: Fast and Slow pointers.

Cualquier numero sera llamado numero feliz si, despues de reemplazarlo repetidamente con un numero igual a la suma del cuadrado de todos sus digitos, nos lleva al numero "1". Todos los demas numeros (no felices) nunca llegaran a "1". En su lugar, estaran atrapados en un ciclo de numeros que no incluye "1".

Input: 23

Output: true (23 is a happy number)

Ejemplo:

1.2 + 3 = 4 + 9 = 13 
2.1 + 3 = 1 + 9 = 10 
3.1 + 0 = 1 + 0 = 1


def find_happy_number(num):
  slow, fast = num, num
  while True:
    slow = find_square_sum(slow)
    fast = find_square_sum(find_square_sum(fast))
    if slow == fast:
      break
  return slow == 1 


def find_square_sum(num):
  _sum = 0
  while (num > 0):
    digit = num % 10
    _sum += digit * digit
    num //= 10
  return _sum


def main():
  print(find_happy_number(23))
  print(find_happy_number(12))

main()
