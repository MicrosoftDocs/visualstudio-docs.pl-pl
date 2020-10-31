---
title: Węzły tekstury
description: Dowiedz się więcej na temat węzłów tekstury, które mają przykładowe różne typy tekstury i geometrie, a następnie Wygeneruj lub Przekształć Współrzędne tekstury w projektancie cieniowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3e45789358e49a0b224a6de3ea6e5dfea44bf01
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93133965"
---
# <a name="texture-nodes"></a>Węzły tekstury

W projektancie programu do cieniowania węzły tekstury przykładą różne typy tekstury i geometrie, a także tworzą lub przekształcają Współrzędne tekstury. Tekstury zapewniają szczegółowe informacje o kolorach i oświetleniu obiektów.

## <a name="texture-node-reference"></a>Odwołanie do węzła tekstury

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Przykład mapy sześciennej**|Pobiera próbkę koloru z mapy sześciennej na określonych współrzędnych.<br /><br /> Możesz użyć mapy sześciennej, aby podać szczegóły koloru dla efektów odbicia lub zastosować do obiektu sferycznego teksturę, która ma mniej zniekształceń niż tekstura 2D.<br /><br /> **Klawiatur**<br /><br /> `UVW`: `float3`<br /> Wektor, który określa lokalizację w module tekstury, w którym jest pobierana próbka. Próbkowanie jest wykonywane, gdy wektor przecina moduł.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Przykład koloru.|**Tekstura**<br /> Rejestr tekstury skojarzony z próbnikiem.|
|**Przykładowa Mapa normalna**|Pobiera normalną próbkę z mapy normalnej 2D na określonych współrzędnych<br /><br /> Można użyć mapy normalnej do symulowania wyglądu dodatkowych geometrycznych szczegółów na powierzchni obiektu. Mapy normalne zawierają spakowane dane, które reprezentują wektor jednostki zamiast danych koloru<br /><br /> **Klawiatur**<br /><br /> `UV`: `float2`<br /> Współrzędne, w których pobierana jest próbka.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float3`<br /> Normalny przykład.|**Dopasowanie osi**<br /> Współczynnik używany do dostosowania skrętności przykładu mapy normalnej.<br /><br /> **Tekstura**<br /> Rejestr tekstury skojarzony z próbnikiem.|
|**Przesuń UV**|Pans określone współrzędne tekstury jako funkcję czasu.<br /><br /> Można jej użyć do przenoszenia tekstury lub mapy normalnej na powierzchni obiektu.<br /><br /> **Klawiatur**<br /><br /> `UV`: `float2`<br /> Współrzędne do kadrowania.<br /><br /> `Time`: `float`<br /> Długość czasu, przez który następuje przesunięcie (w sekundach).<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float2`<br /> Współrzędne przesuwane.|**Szybkość X**<br /> Liczba tekseli, które są przesuwane wzdłuż osi x na sekundę.<br /><br /> **Szybkość Y**<br /> Liczba tekseli, które są przesuwane wzdłuż osi y na sekundę.|
|**Paralaksy UV**|Umieszcza określone współrzędne tekstury jako funkcję wysokooci i kąt wyświetlania.<br /><br /> Ten efekt jest znany jako *Mapowanie paralaksy* lub wirtualne mapowanie przemieszczenia. Można go użyć do utworzenia iluzji głębokości na płaskiej powierzchni.<br /><br /> **Klawiatur**<br /><br /> `UV`: `float2`<br /> Współrzędne do przemieszczenia.<br /><br /> `Height`: `float`<br /> Wartość heightmap, która jest skojarzona ze `UV` współrzędnymi.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float2`<br /> Współrzędne przemieszczenia.|**Płaszczyzna głębokości**<br /> Głębokość odniesienia dla efektu paralaksy. Wartość domyślna to 0,5. Mniejsze wartości zmniejszają teksturę; większe wartości ujścia do powierzchni.<br /><br /> **Skala głębokości**<br /> Skala efektu paralaksy. Sprawia to, że pozorna głębokość jest większa lub mniejsza. Typowe wartości mieszczą się w zakresie od 0,02 do 0,1.|
|**Obróć UV**|Obraca określone współrzędne tekstury wokół punktu centralnego jako funkcję czasu.<br /><br /> Można jej użyć do obracania tekstury lub mapy normalnej na powierzchni obiektu.<br /><br /> **Klawiatur**<br /><br /> `UV`: `float2`<br /> Współrzędne do obrotu.<br /><br /> `Time`: `float`<br /> Długość czasu, przez który następuje przesunięcie (w sekundach).<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float2`<br /> Obrócone współrzędne.|**Wyśrodkuj X**<br /> Współrzędna x definiująca środek obrotu.<br /><br /> **Wyśrodkuj na osi Y**<br /> Współrzędna y definiująca środek obrotu.<br /><br /> **Szybkość**<br /> Kąt w radianach, przez który tekstura obraca się na sekundę.|
|**Współrzędna tekstury**|Współrzędne tekstury bieżącego piksela.<br /><br /> Współrzędne tekstury są określane przez interpolację między atrybutami współrzędnej tekstury pobliskich wierzchołków. Można to traktować jako pozycję bieżącego piksela w przestrzeni tekstury.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float2`<br /> Współrzędne tekstury.|Brak|
|**Wymiary tekstury**|Wyświetla szerokość i wysokość mapy tekstury 2D.<br /><br /> Można użyć wymiarów tekstury, aby rozważyć szerokość i wysokość tekstury w module cieniującego.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float2`<br /> Szerokość i wysokość tekstury wyrażona jako wektor. Szerokość jest przechowywana w pierwszym elemencie wektora. Wysokość jest przechowywana w drugim elemencie.|**Tekstura**<br /> Rejestr tekstury skojarzony z wymiarami tekstury.|
|**Delta Texel**|Wyprowadza różnicę (odległość) między tekseli mapy tekstury 2D.<br /><br /> Możesz użyć delty Texel do próbkowania sąsiadujących wartości Texel w module cieniującego.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float2`<br /> Różnica (odległość) od Texel do następnego Texel (przesuwana ukośnie w kierunku pozytywnym), wyrażona jako wektor w znormalizowanym obszarze tekstury. Można utworzyć pozycje wszystkich sąsiednich tekseli przez wybiórcze ignorowanie lub negację współrzędnych zmiany U lub V.|**Tekstura**<br /> Rejestr tekstury skojarzony z różnicą Texel.|
|**Przykład tekstury**|Pobiera próbkę koloru z mapy tekstury 2D na określonych współrzędnych.<br /><br /> Mapa tekstury służy do zapewniania szczegółów koloru na powierzchni obiektu.<br /><br /> **Klawiatur**<br /><br /> `UV`: `float2`<br /> Współrzędne, w których pobierana jest próbka.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Przykład koloru.|**Tekstura**<br /> Rejestr tekstury skojarzony z próbnikiem.|
