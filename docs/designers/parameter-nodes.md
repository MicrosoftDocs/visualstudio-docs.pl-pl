---
title: Węzły parametrów
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f749d4ed6338919132e1c48d6da0572e3efe88
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635019"
---
# <a name="parameter-nodes"></a>Węzły parametrów

W Projektancie modułu cieniującego węzły parametrów reprezentują dane wejściowe do modułu cieniującego, które znajdują się pod kontrolą aplikacji na podstawie na rysowanie, na przykład właściwości materiału, światła kierunkowe, położenie kamery i czas. Ponieważ można zmienić te parametry przy każdym wywołaniu rysowania, można użyć tego samego modułu cieniującego, aby nadać obiektowi różne wyglądy.

## <a name="parameter-node-reference"></a>Odwołanie do węzła parametru

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Pozycja kamery na świecie**|Położenie kamery w przestrzeni światowej.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Położenie kamery.|Brak|
|**Kierunek światła**|Wektor definiujący kierunek, w którym światło jest odlewane ze źródła światła w przestrzeni świata.<br /><br /> Można go użyć do obliczenia oświetlenia i wkładu spekulacyjnych w przestrzeni światowej.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do źródła światła.|Brak|
|**Otoczenie materiału**|Rozproszony wkład kolorów bieżącego piksela, który jest przypisany do oświetlenia pośredniego.<br /><br /> Rozproszony kolor piksela symuluje sposób interakcji oświetlenia z szorstkimi powierzchniami. Za pomocą parametru Otoczenie materiału można przybliżyć, w jaki sposób oświetlenie pośrednie przyczynia się do pojawienia się obiektu w świecie rzeczywistym.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Rozproszony kolor bieżącego piksela, który jest spowodowany pośrednim — czyli oświetleniem otoczenia.|**Dostęp**<br /> **Publiczne,** aby umożliwić właściwość, która ma być ustawiona z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość**<br /> Rozproszony kolor bieżącego piksela, który jest spowodowany pośrednim — czyli oświetleniem otoczenia.|
|**Materiał rozproszony**|Kolor opisujący sposób rozpraszania bieżącego piksela przez oświetlenie bezpośrednie.<br /><br /> Rozproszony kolor piksela symuluje sposób interakcji oświetlenia z szorstkimi powierzchniami. Za pomocą parametru Materiał rozproszony można zmienić sposób rozpraszania bieżącego piksela przez bezpośrednie oświetlenie , czyli kierunkowe, punktowe i punktowe.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Kolor opisujący sposób rozpraszania bieżącego piksela przez oświetlenie bezpośrednie.|**Dostęp**<br /> **Publiczne,** aby umożliwić właściwość, która ma być ustawiona z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość**<br /> Kolor opisujący sposób rozpraszania bieżącego piksela przez oświetlenie bezpośrednie.|
|**Materiał Emissive**|Wkład kolorów bieżącego piksela, który jest przypisany do oświetlenia, które dostarcza do siebie.<br /><br /> Można użyć tego do symulacji świecącego obiektu; to znaczy przedmiot, który dostarcza własne światło. To światło nie wpływa na inne obiekty.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Wkład kolorów bieżącego piksela, który jest spowodowany własnym oświetleniem.|**Dostęp**<br /> **Publiczne,** aby umożliwić właściwość, która ma być ustawiona z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość**<br /> Wkład kolorów bieżącego piksela, który jest spowodowany własnym oświetleniem.|
|**Materiał Specular**|Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.<br /><br /> Kolor lustrzany piksela symuluje sposób interakcji oświetlenia z gładkimi, lustrzanymi powierzchniami. Za pomocą parametru Material Specular można zmienić sposób, w jaki bieżący piksel odbija bezpośrednie oświetlenie , czyli kierunkowe, punktowe i punktowe.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.|**Dostęp**<br /> **Publiczne,** aby umożliwić właściwość, aby ustawić z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość**<br /> Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.|
|**Moc lustrzana materiału**|Wartość skalarna opisująca intensywność świateł lustrzanych.<br /><br /> Im większa moc odchudkowa, tym bardziej intensywne i dalekosiężne stają się światła lustrzane.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float`<br /> Wykładniczy termin opisujący intensywność świateł lustrzanych w bieżącym pikselu.|**Dostęp**<br /> **Publiczne,** aby umożliwić właściwość, która ma być ustawiona z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość**<br /> Wykładnik definiujący intensywność świateł lustrzanych w bieżącym pikselu.|
|**Znormalizowany czas**|Czas w sekundach, znormalizowany do zakresu [0, 1], tak, że gdy czas osiągnie 1, resetuje się do 0.<br /><br /> Można go użyć jako parametru w obliczeniach modułu cieniującego, na przykład do animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float`<br /> Znormalizowany czas w sekundach.|Brak|
|**Czas**|Czas w sekundach.<br /><br /> Można go użyć jako parametru w obliczeniach modułu cieniującego, na przykład do animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float`<br /> Czas, w sekundach.|Brak|