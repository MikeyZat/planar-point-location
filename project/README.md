# Dokumentacja

### Klasy użyte na potrzeby realizacji algorytmu:

- `Point` - reprezentuje punkt w przestrzeni za pomocą współrzędnych `x` i `y`
- `Segment` - reprezentuje odcinek w przestrzeni za pomocą `start` i `end` typu `Point`, gdzie zawsze `start.x <= end.x`
- `Trapezoid` - reprezentuje trapez w sposób jaki jest potrzebny do realizacji algorytmu:
   > `leftp` = Punkt lewej krawędzi \
   > `rightp` = Punkt prawej krawędzi (punkt) \
   > `top` = Górna krawędź (odcinek) \
   > `bottom` = Dolna krawędź (odcinek)\
   > `left_top` = Wskaźnik do lewego, górnego sąsiada (jeśli brak sąsiada to `None`)\
   > `left_bottom` = Wskaźnik do lewego, dolnego sąsiada (jeśli brak sąsiada to `None`)\
   > `right_bottom` = Wskaźnik do prawego, dolnego sąsiada (jeśli brak sąsiada to `None`)\
   > `right_top` = Wskaźnik do prawego, górnego sąsiada (jeśli brak sąsiada to `None`)\
   > `node` = Wskaźnik do odpowiadającego węzła w grafie
- `Node` - Węzeł w grafie acyklicznym skierowanym. Cechuje go:
    - typ (ściana `WALL` | x-węzeł `X_NODE` | y-wezęł `Y_NODE`), \
    - value (odpowiednio: trapez, punkt, odcinek)
    - wskaźniki do lewego i prawego dziecka oraz do rodzica
- `Graph` - acykliczny graf skierowany służący jako graf wyszukiwania. Posiada metody:
    > `find(point_to_find)` Zwraca trapez, który zawiera dany punkt lub -1
     jeśli procedura nie powiodła się \
    > `add_trapezoid(trapezoid, new_node)` - zamienia w grafie węzeł reprezentujący `trapezoid`
    na nową strukturę `new_node`
    >