---
title: Stałe węzły
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86fd5a9b2d179a27ec0cf34f5388b30ebb563ad4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637354"
---
# <a name="constant-nodes"></a>Stałe węzły

W projektancie programu do cieniowania stałe węzły reprezentują wartości literałów i interpolowane atrybuty wierzchołka w obliczeniach cieniowania pikseli. Ponieważ atrybuty wierzchołków są interpolowane — i dlatego są różne dla każdego piksela — każde wystąpienie programu do cieniowania pikseli otrzymuje inną wersję stałej. Dzięki temu każdy piksel ma unikatowy wygląd.

## <a name="vertex-attribute-interpolation"></a>Interpolacja atrybutu wierzchołka

Obraz sceny 3D w grze lub aplikacji jest realizowany przez matematycznie przekształcanie wielu obiektów, które są definiowane przez wierzchołki, atrybuty wierzchołków i definicje pierwotne — do pikseli na ekranie. Wszystkie informacje, które są wymagane do uzyskania piksela jego unikatowego wyglądu, są dostarczane za pomocą atrybutów wierzchołków, które są połączone ze sobą, w zależności od odległości do różnych wierzchołków, które tworzą *pierwotną*. Element podstawowy jest podstawowym elementem renderingu; oznacza to prosty kształt, taki jak punkt, linia lub trójkąt. Piksel, który jest blisko tylko jeden z wierzchołków odbiera stałe, które są niemal identyczne z tym wierzchołkiem, ale piksel, który jest równomiernie rozłożony między wszystkimi wierzchołkami elementu pierwotnego, który jest średnią z tych wierzchołków. W programowaniu grafiki, stałe, które otrzymują piksele, są uważane za *interpolowane*. Dostarczanie stałych danych do pikseli w ten sposób zapewnia bardzo dobrą jakość wizualną i w tym samym czasie zmniejsza wymagania dotyczące pamięci i przepustowości.

Chociaż każde wystąpienie programu do cieniowania pikseli otrzymuje tylko jeden zestaw wartości stałych i nie może zmienić tych wartości, różne wystąpienia programu do cieniowania pikseli otrzymują różne zestawy danych stałych. Ten projekt umożliwia programowi cieniującego wygenerowanie różnych danych wyjściowych koloru dla każdego piksela w pierwotnym.

## <a name="constant-node-reference"></a>Odwołanie do węzła stałego

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Wektor kamery**|Wektor, który rozciąga się od bieżącego piksela do kamery w przestrzeni świata.<br /><br /> Można go użyć do obliczenia odbić w przestrzeni świata.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do aparatu.|Brak|
|**Stała koloru**|Stała wartość koloru.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Wartość koloru.|**Output**<br /> Wartość koloru.|
|**Stałego**|Stała wartość skalarna.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Wartość skalarna.|**Output**<br /> Wartość skalarna.|
|**Stała 2D**|Stała wektora dwuskładnikowego.<br /><br /> **Output**<br /><br /> `Output`: `float2`<br /> Wartość wektora.|**Output**<br /> Wartość wektora.|
|**Stała 3D**|Stała wektora z trzema składnikami.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Wartość wektora.|**Output**<br /> Wartość wektora.|
|**Stała 4D**|Stała wektorowa z czterema składnikami.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Wartość koloru.|**Output**<br /> Wartość wektora.|
|**Pozycja znormalizowana**|Pozycja bieżącego piksela wyrażona w znormalizowanych współrzędnych urządzenia.<br /><br /> Współrzędna x i Współrzędne y mają wartości z zakresu [-1, 1], Współrzędna z zakresu [0, 1], a składnik w zawiera wartość głębokości punktu w obszarze widoku. w nie jest znormalizowana.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Pozycja bieżącego piksela.|Brak|
|**Kolor punktu**|Kolor rozpraszania bieżącego piksela, który jest kombinacją koloru rozpraszanego materiału i atrybutów koloru wierzchołka.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Kolor rozpraszania bieżącego piksela.|Brak|
|**Głębokość punktu**|Głębokość bieżącego piksela w obszarze widoku.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Głębokość bieżącego piksela.|Brak|
|**Znormalizowana głębokość punktu**|Głębokość bieżącego piksela wyrażona w znormalizowanych współrzędnych urządzenia.<br /><br /> Wynik ma wartość z zakresu [0, 1].<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Głębokość bieżącego piksela.|Brak|
|**Pozycja ekranu**|Pozycja bieżącego piksela wyrażona we współrzędnych ekranu.<br /><br /> Współrzędne ekranu opierają się na bieżącym okienku ekranu. Składniki x i y zawierają współrzędne ekranu, składnik między z zawiera głębię znormalizowaną do zakresu [0, 1], a składnik w zawiera wartość głębokości w obszarze widoku.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Pozycja bieżącego piksela.|Brak|
|**Normalne powierzchni**|Normalne powierzchni bieżącego piksela w przestrzeni obiektów.<br /><br /> Za pomocą tego programu można obliczyć wkłady i odbicia oświetlenia w przestrzeni obiektów.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Normalne powierzchni bieżącego piksela.|Brak|
|**Wektor kamery przestrzeni stycznej**|Wektor, który rozciąga się od bieżącego piksela do kamery w przestrzeni stycznej.<br /><br /> Można go użyć do obliczenia odbić w przestrzeni stycznej.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do aparatu.|Brak|
|**Kierunek światła przestrzeni stycznej**|Wektor definiujący kierunek rzutowania światła ze źródła światła w przestrzeni stycznej bieżącego piksela.<br /><br /> Można jej użyć do obliczenia odblasków i współtworzenia w przestrzeni stycznej.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do źródła światła.|Brak|
|**Normalna świata**|Normalne powierzchni bieżącego piksela w przestrzeni świata.<br /><br /> Można jej użyć do obliczenia wkładów oświetlenia i odbicia w przestrzeni świata.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Normalne powierzchni bieżącego piksela.|Brak|
|**Pozycja świata**|Pozycja bieżącego piksela w przestrzeni świata.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Pozycja bieżącego piksela.|Brak|