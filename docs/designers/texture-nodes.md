---
title: Węzły tekstury
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73f5bfe71866422cd3717c2a29f1eeb48d15cc76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844219"
---
# <a name="texture-nodes"></a>Węzły tekstury

W projektancie programu do cieniowania węzły tekstury przykładowy różne typy tekstury i geometrii, tworzyć i przekształcenia współrzędnych tekstury. Tekstury zapewniają kolorów i oświetlenia szczegółów obiektów.

## <a name="texture-node-reference"></a>Odwołanie do węzła tekstury

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Przykładowa mapa sześcienna**|Pobiera próbkę koloru z mapy sześciennej na określonych współrzędnych.<br /><br /> Można użyć mapy sześciennej, aby udostępnić szczegóły koloru na potrzeby efektów odbicia lub aby zastosować dla kulistego obiektu teksturę, która ma zniekształceniami niż w przypadku tekstury 2W.<br /><br /> **Dane wejściowe:**<br /><br /> `UVW`: `float3`<br /> Wektor, który określa lokalizację w module tekstury, gdzie próbki. Próbka jest pobierana, gdzie to wektor przecina modułu.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Przykład koloru.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem.|
|**Przykładowa mapa normalna**|Pobiera próbkę normalną z mapy normalnej 2W na określonych współrzędnych<br /><br /> Można użyć mapy normalnej do symulowania wyglądu dodatkowych szczegółów geometrycznych na powierzchni obiektu. Mapy normalne zawierają spakowane dane, które reprezentuje wektor jednostki, a nie dane koloru<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne, w którym próbki.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Przykład normalny.|**Dostosowanie osi**<br /> Czynnik, który jest używany do dostosowania skrętności dla próbki mapy normalnej.<br /><br /> **Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem.|
|**Przesuń mapowanie UV**|Miednice określonego tekstury koordynuje w funkcji czasu.<br /><br /> Służy to do przesunięcia tekstury lub mapy normalnej na powierzchni obiektu.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne, aby przesunąć.<br /><br /> `Time`: `float`<br /> Długość czasu, aby przesunąć, w ciągu kilku sekund.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Współrzędne panned.|**Prędkość w osi X**<br /> Liczba tekseli przesuwanych wzdłuż osi x na sekundę.<br /><br /> **Prędkość w osi Y**<br /> Liczba tekseli przesuwanych wzdłuż osi y na sekundę.|
|**Równoległe mapowanie UV**|Powoduje przemieszczenie współrzędnych tekstury określona w funkcji wysokości i kąta widzenia.<br /><br /> Efekt, spowoduje to utworzenie jest znany jako *mapowanie równoległe*, lub mapowanie przemieszczenia wirtualnego. Można go użyć do utworzenia iluzji głębi w przypadku płaskiej powierzchni.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne się wykluczają.<br /><br /> `Height`: `float`<br /> Wartość heightmap, która jest skojarzona z `UV` współrzędnych.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Przesuniętą współrzędne.|**Płaszczyzna głębi**<br /> Głębokość odniesienia dla efektu równoległe. Domyślna wartość wynosi 0,5. Mniejsze wartości Podnieś teksturę. większe jej zapadanie w powierzchnię.<br /><br /> **Skala głębi**<br /> Skala efekt równoległe. Dzięki temu bardziej lub mniej wyraźnego głębi. Typowe wartości z zakresu od 0,02 do 0,1.|
|**Obróć mapowanie UV**|Obraca się współrzędnych tekstury określonego wokół punktu centralnego w funkcji czasu.<br /><br /> Służy to do obrócenia tekstury lub mapy normalnej na powierzchni obiektu.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne wymiany.<br /><br /> `Time`: `float`<br /> Długość czasu, aby przesunąć, w ciągu kilku sekund.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Obrócony współrzędne.|**Współrzędnej X środka**<br /> Współrzędna x definiująca środek obrotu.<br /><br /> **Wyśrodkuj na osi Y**<br /> Współrzędna y definiująca środek obrotu.<br /><br /> **szybkość**<br /> Kąt w radianach, przez który Tekstura obraca się w ciągu sekundy.|
|**Współrzędna tekstury**|Współrzędne tekstury bieżącego piksela.<br /><br /> Współrzędne tekstury są określane przez interpolacji między atrybutów współrzędnych tekstury pobliskich wierzchołków. To można traktować jako pozycję bieżącego piksela w przestrzeni tekstury.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Współrzędne tekstury.|Brak|
|**Wymiary tekstury**|Dane wyjściowe, szerokość i wysokość mapy tekstury 2W.<br /><br /> Wymiary tekstury umożliwia należy wziąć pod uwagę szerokość i wysokość tekstury w modułu cieniującego.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Szerokość i wysokość tekstury, wyrażone jako wektor. Szerokość znajduje się w pierwszym elemencie wektora. Wysokość jest przechowywany w elemencie drugiego.|**Tekstury**<br /> Rejestr tekstury skojarzony z wymiarów tekstury.|
|**Texel Delta**|Generuje różnicowej (odległość) między tekseli mapy tekstury 2W.<br /><br /> Delta teksela służy do próbkowania sąsiadujących wartości texel w module cieniującym.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Delta (odległość) z teksela do dalej teksela (przenoszenie po przekątnej w kierunku dodatnią,), wyrażone jako wektor w przestrzeni tekstury znormalizowana. Pochodzi z pozycji wszystkie tekseli sąsiednich, selektywnie ignorowanie lub Negacja współrzędne U lub V różnicowej.|**Tekstury**<br /> Rejestr tekstury skojarzony z delty teksela.|
|**Próbki tekstury**|Pobiera próbkę koloru z mapy tekstury 2D na określonych współrzędnych.<br /><br /> Można użyć mapy tekstury, aby udostępnić szczegóły koloru na powierzchni obiektu.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne, w którym próbki.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Przykład koloru.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem.|