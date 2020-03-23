---
title: Węzły tekstury
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3393bb979b73694c4ac65120ae794ef1205b37c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589816"
---
# <a name="texture-nodes"></a>Węzły tekstury

W Projektancie modułu cieniującego węzły tekstur próbkują różne typy i geometrie tekstur oraz tworzą lub przekształcają współrzędne tekstury. Tekstury zapewniają kolor i szczegóły oświetlenia obiektów.

## <a name="texture-node-reference"></a>Odwołanie do węzła tekstury

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Przykład mapy modułu**|Pobiera próbkę koloru z mapy modułu w określonych współrzędnych.<br /><br /> Można użyć mapy modułu, aby zapewnić szczegóły kolorów dla efektów odbicia lub zastosować do obiektu sferycznego teksturę, która ma mniejsze zniekształcenia niż tekstura 2D.<br /><br /> **Dane wejściowe:**<br /><br /> `UVW`: `float3`<br /> Wektor, który określa lokalizację na module tekstury, w którym pobierana jest próbka. Próbka jest pobierana, gdy ten wektor przecina moduł.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Próbka koloru.|**Tekstura**<br /> Rejestr tekstur, który jest skojarzony z próbnikem.|
|**Normalna próbka mapy**|Pobiera normalną próbkę z normalnej mapy 2D w określonych współrzędnych<br /><br /> Można użyć mapy normalnej, aby symulować wygląd dodatkowych szczegółów geometrycznych na powierzchni obiektu. Normalne mapy zawierają spakowane dane reprezentujące wektor jednostkowy zamiast danych kolorów<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne, w których pobierana jest próbka.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Normalna próbka.|**Regulacja osi**<br /> Współczynnik, który jest używany do dostosowania rozdania normalnej próbki mapy.<br /><br /> **Tekstura**<br /> Rejestr tekstur, który jest skojarzony z próbnikem.|
|**Pan UV**|Przesuwa określone współrzędne tekstury jako funkcję czasu.<br /><br /> Można użyć tego, aby przenieść teksturę lub normalną mapę na powierzchnię obiektu.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne do przesuwania.<br /><br /> `Time`: `float`<br /> Czas przesuwania się w sekundach.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Współrzędne.|**Prędkość X**<br /> Liczba texels, które są przesuwane wzdłuż osi x, na sekundę.<br /><br /> **Prędkość Y**<br /> Liczba texels, które są przesuwane wzdłuż osi y, na sekundę.|
|**Paralaksa UV**|Wypiera określone współrzędne tekstury jako funkcję wysokości i kąta widzenia.<br /><br /> Efekt, który to tworzy jest znany jako *mapowanie paralaksy*lub wirtualne mapowanie przemieszczenia. Można go użyć do stworzenia iluzji głębi na płaskiej powierzchni.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne do wypierki.<br /><br /> `Height`: `float`<br /> Wartość mapy wysokości skojarzona ze `UV` współrzędnymi.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Przesunięte współrzędne.|**Płaszczyzna głębokości**<br /> Głębokość odniesienia dla efektu paralaksy. Domyślnie wartość wynosi 0,5. Mniejsze wartości podnoszą teksturę; większe wartości zatopić go w powierzchni.<br /><br /> **Skala głębokości**<br /> Skala efektu paralaksy. To sprawia, że widoczna głębokość jest mniej lub bardziej wyraźna. Typowe wartości wahają się od 0,02 do 0,1.|
|**Obróć UV**|Obraca określone współrzędne tekstury wokół punktu centralnego jako funkcję czasu.<br /><br /> Można użyć tej funkcji, aby obrócić teksturę lub normalną mapę na powierzchni obiektu.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne do obracania.<br /><br /> `Time`: `float`<br /> Czas przesuwania się w sekundach.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Obróconych współrzędnych.|**Środek X**<br /> Współrzędna x definiująca środek obrotu.<br /><br /> **Środek Y**<br /> Współrzędna y definiująca środek obrotu.<br /><br /> **Szybkość**<br /> Kąt w radianach, pod którym tekstura obraca się na sekundę.|
|**Współrzędne tekstury**|Współrzędne tekstury bieżącego piksela.<br /><br /> Współrzędne tekstury są określane przez interpolację między atrybutami współrzędnych tekstury pobliskich wierzchołków. Można to potraktować jako położenie bieżącego piksela w przestrzeni tekstury.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Współrzędne tekstury.|Brak|
|**Wymiary tekstury**|Wyprowadza szerokość i wysokość mapy tekstury 2D.<br /><br /> Za pomocą wymiarów tekstury można wziąć pod uwagę szerokość i wysokość tekstury w modułie cieniującym.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Szerokość i wysokość tekstury, wyrażona jako wektor. Szerokość jest przechowywana w pierwszym elemencie wektora. Wysokość jest przechowywana w drugim elemencie.|**Tekstura**<br /> Rejestr tekstur skojarzony z wymiarami tekstury.|
|**Texel Delta**|Wyprowadza delta (odległość) między texels mapy tekstury 2D.<br /><br /> Za pomocą delta texel można pobrać próbkę sąsiednich wartości texel w modułie cieniującym.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Delta (odległość) od texel do następnego texel (poruszający się po przekątnej w kierunku dodatnim), wyrażona jako wektor w znormalizowanej przestrzeni tekstury. Pozycje wszystkich sąsiednich texels można wyprowadzić, wybiórczo ignorując lub negując współrzędne U lub V delta.|**Tekstura**<br /> Rejestr tekstur, który jest skojarzony z delta texel.|
|**Próbka tekstury**|Pobiera próbkę koloru z mapy tekstury 2D w określonych współrzędnych.<br /><br /> Można użyć mapy tekstury, aby zapewnić szczegóły koloru na powierzchni obiektu.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne, w których pobierana jest próbka.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Próbka koloru.|**Tekstura**<br /> Rejestr tekstur, który jest skojarzony z próbnikem.|
