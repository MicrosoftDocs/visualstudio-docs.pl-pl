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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72637354"
---
# <a name="constant-nodes"></a>Stałe węzły

W Projektancie modułu cieniującego stałe węzły reprezentują wartości literału i interpolowane atrybuty wierzchołka w obliczeniach modułu cieniującego pikseli. Ponieważ atrybuty wierzchołka są interpolowane — a więc są różne dla każdego piksela — każde wystąpienie modułu cieniującego pikseli otrzymuje inną wersję stałej. Daje to każdemu pikselowi niepowtarzalny wygląd.

## <a name="vertex-attribute-interpolation"></a>Interpolacja atrybutów wierzchołka

Obraz sceny 3D w grze lub aplikacji jest wykonany przez matematyczne przekształcanie wielu obiektów , które są definiowane przez wierzchołki, atrybuty wierzchołków i pierwotne definicje , w piksele ekranowe. Wszystkie informacje, które są wymagane do nadanie pikselowi jego niepowtarzalnego wyglądu, są dostarczane za pośrednictwem atrybutów wierzchołków, które są mieszane ze sobą w zależności od bliskości piksela do różnych wierzchołków, które składają się na jego *prymitywne*. Element pierwotny jest podstawowym elementem renderowania; to znaczy prosty kształt, taki jak punkt, linia lub trójkąt. Piksel, który jest bardzo blisko tylko jeden z wierzchołków otrzymuje stałe, które są prawie identyczne z tym wierzchołkiem, ale piksel, który jest równomiernie rozmieszczony między wszystkimi wierzchołkami pierwotnego otrzymuje stałe, które są średnie z tych wierzchołków. W programowaniu graficznym, stałe, które piksele otrzymują są uważane za *interpolowane*. Dostarczanie stałych danych pikselom w ten sposób zapewnia bardzo dobrą jakość obrazu, a jednocześnie zmniejsza zużycie pamięci i wymagania dotyczące przepustowości.

Mimo że każde wystąpienie modułu cieniującego pikseli otrzymuje tylko jeden zestaw wartości stałych i nie może zmienić tych wartości, różne wystąpienia modułu cieniującego pikseli otrzymują różne zestawy stałych danych. Ten projekt umożliwia programowi cieniującemu tworzenie różnych danych wyjściowych kolorów dla każdego piksela w prymitywnym.

## <a name="constant-node-reference"></a>Odwołanie do węzła stałego

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Wektor kamery**|Wektor, który rozciąga się od bieżącego piksela do kamery w przestrzeni światowej.<br /><br /> Można go użyć do obliczania odbić w przestrzeni świata.<br /><br /> **Wyjście**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do kamery.|Brak|
|**Stała kolorów**|Stała wartość koloru.<br /><br /> **Wyjście**<br /><br /> `Output`: `float4`<br /> Wartość koloru.|**Wyjście**<br /> Wartość koloru.|
|**Stały**|Stała wartość skalarna.<br /><br /> **Wyjście**<br /><br /> `Output`: `float`<br /> Wartość skalarna.|**Wyjście**<br /> Wartość skalarna.|
|**Stała 2D**|Dwuskładnikowa stała wektorowa.<br /><br /> **Wyjście**<br /><br /> `Output`: `float2`<br /> Wartość wektora.|**Wyjście**<br /> Wartość wektora.|
|**Stała 3D**|Trzyskładnikowa stała wektorowa.<br /><br /> **Wyjście**<br /><br /> `Output`: `float3`<br /> Wartość wektora.|**Wyjście**<br /> Wartość wektora.|
|**Stała 4D**|Czteroskładnikowa stała wektorowa.<br /><br /> **Wyjście**<br /><br /> `Output`: `float4`<br /> Wartość koloru.|**Wyjście**<br /> Wartość wektora.|
|**Pozycja znormalizowana**|Położenie bieżącego piksela wyrażone we współrzędnych urządzenia znormalizowanego.<br /><br /> Współrzędne x i współrzędne y mają wartości w zakresie [-1, 1], współrzędna z ma wartość w zakresie [0, 1], a komponent w zawiera wartość głębokości punktu w przestrzeni widoku; w nie jest znormalizowana.<br /><br /> **Wyjście**<br /><br /> `Output`: `float4`<br /> Położenie bieżącego piksela.|Brak|
|**Kolor punktu**|Rozproszony kolor bieżącego piksela, który jest kombinacją atrybutów koloru rozproszonego materiału i koloru wierzchołka.<br /><br /> **Wyjście**<br /><br /> `Output`: `float4`<br /> Rozproszony kolor bieżącego piksela.|Brak|
|**Głębokość punktu**|Głębokość bieżącego piksela w przestrzeni widoku.<br /><br /> **Wyjście**<br /><br /> `Output`: `float`<br /> Głębokość bieżącego piksela.|Brak|
|**Znormalizowana głębokość punktu**|Głębokość bieżącego piksela, wyrażona w znormalizowanych współrzędnych urządzenia.<br /><br /> Wynik ma wartość w zakresie [0, 1].<br /><br /> **Wyjście**<br /><br /> `Output`: `float`<br /> Głębokość bieżącego piksela.|Brak|
|**Pozycja ekranu**|Położenie bieżącego piksela, wyrażone we współrzędnych ekranu.<br /><br /> Współrzędne ekranu są oparte na bieżącej rzutni. Komponenty x i y zawierają współrzędne ekranu, komponent z zawiera głębokość znormalizowane do zakresu [0, 1], a składnik w zawiera wartość głębokości w przestrzeni widoku.<br /><br /> **Wyjście**<br /><br /> `Output`: `float4`<br /> Położenie bieżącego piksela.|Brak|
|**Powierzchnia normalna**|Powierzchnia normalna bieżącego piksela w przestrzeni obiektu.<br /><br /> Można go użyć do obliczenia udziału oświetlenia i odbić w przestrzeni obiektu.<br /><br /> **Wyjście**<br /><br /> `Output`: `float3`<br /> Powierzchnia normalna bieżącego piksela.|Brak|
|**Styczna kamera kosmiczna Wektor**|Wektor, który rozciąga się od bieżącego piksela do kamery w przestrzeni stycznej.<br /><br /> Można użyć tego do obliczenia odbić w przestrzeni stycznej.<br /><br /> **Wyjście**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do kamery.|Brak|
|**Kierunek światła stycznego przestrzeni**|Wektor definiujący kierunek, w którym światło jest rzutowe ze źródła światła w przestrzeni stycznej bieżącego piksela.<br /><br /> Można go użyć do obliczenia oświetlenia i wkładu lustrzanego w przestrzeni stycznej.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do źródła światła.|Brak|
|**Świat normalny**|Powierzchnia normalna bieżącego piksela w przestrzeni świata.<br /><br /> Można go użyć do obliczenia wkładu oświetlenia i odbić w przestrzeni światowej.<br /><br /> **Wyjście**<br /><br /> `Output`: `float3`<br /> Powierzchnia normalna bieżącego piksela.|Brak|
|**Pozycja na świecie**|Położenie bieżącego piksela w przestrzeni świata.<br /><br /> **Wyjście**<br /><br /> `Output`: `float4`<br /> Położenie bieżącego piksela.|Brak|