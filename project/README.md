# Dokumentacja

### Klasy użyte na potrzeby realizacji algorytmu:

- `Point` - reprezentuje punkt w przestrzeni za pomocą współrzędnych `x` i `y`
- `Segment` - reprezentuje odcinek w przestrzeni za pomocą `start` i `end` typu `Point`, gdzie zawsze `start.x <= end.x`
- `Trapezoid` - reprezentuje trapez w sposób jaki jest potrzebny do realizacji algorytmu:
   - `leftp` = Punkt lewej krawędzi
   - `rightp` = Punkt prawej krawędzi (punkt)
   - `top` = Górna krawędź (odcinek)
   - `bottom` = Dolna krawędź (odcinek)
   - `left_top` = Wskaźnik do lewego, górnego sąsiada (jeśli brak sąsiada to `None`)
   - `left_bottom` = Wskaźnik do lewego, dolnego sąsiada (jeśli brak sąsiada to `None`)
   - `right_bottom` = Wskaźnik do prawego, dolnego sąsiada (jeśli brak sąsiada to `None`)
   - `right_top` = Wskaźnik do prawego, górnego sąsiada (jeśli brak sąsiada to `None`)
   - `node` = Wskaźnik do odpowiadającego węzła w grafie
 
- `Node` - Węzeł w grafie acyklicznym skierowanym. Cechuje go:
    - typ (ściana `WALL` | x-węzeł `X_NODE` | y-wezęł `Y_NODE`), 
    - value (odpowiednio: trapez, punkt, odcinek)
    - wskaźniki do lewego i prawego dziecka oraz do rodzica

- `Graph` - acykliczny graf skierowany służący jako graf wyszukiwania. Jego oczekiwany
 rozmiar jest rzędu O(n). Posiada metody:
    - `find(point_to_find)` Zwraca trapez, który zawiera dany punkt lub -1
     jeśli procedura nie powiodła się. Złożoność czasowa tej metody O(log n).
    - `add_trapezoid(trapezoid, new_node)` - zamienia w grafie węzeł reprezentujący `trapezoid`
    na nową strukturę `new_node. Złożoność czasowa tej operacji to O(1).

### Funkcje realizujące algorytm:


| Nazwa funkcji            | Krótki opis                                                                                                                 | Argumenty                                                             | Zwracana wartość                      | Złożoność czasowa |                                                                   
| -------------------------| ----------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|-------------------|
| `find_point_location`    | Realizuje cały algorytm. Tworzy mapę trapezową, strukturę wyszukiwań, zwraca szukany punkt oraz tworzy dane do wizualizacji.| (point_to_find, segments, MAX_Y, MIN_Y, MAX_X, MIN_X)                 | trapezoid, scenes                     | O(n*logn)         |
| `new_segment_in_map`     | Przetwarza nowy odcinek i aktualizująca wszystkie struktury.                                                                | (trapezoid_containing_first_point, new_segment, visual_representation)| None                                  | O(1)              |
| `update_map`             | Aktualizuje mapę trapezową.                                                                                                 | (trapezoid_to_update, segment, orientation, old_trapezoid, res)       | None                                  | O(1)              |
| `create_new_node`        | Tworzy nowy węzeł w celu zaktualizowania struktury wyszukiwań.                                                              | (...)                                                                 | (Node) new_node                       | O(1)              |
| `prepare_data`           | Przygotowuje dane na potrzeby algorytmu.                                                                                    | (segments //as lists )                                                | [Segment], MAX_Y, MIN_Y, MAX_X, MIN_X | O(n)              |
| `draw_collection`        | Zwraca dane łatwe do wizualizacji.                                                                                          | (elements //as objects)                                               | elements_as_lists                     | O(n)              |
| `is_above_segment`       | Odpowiada na pytanie czy dany odcinek leży nad (po lewej stronie) odcinka.                                                  | (point_to_check, segment)                                             | `True` or `False`                     | O(1)              |