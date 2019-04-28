---
title: Węzły parametrów
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c99986b65e1b396a92e667ceb4eeff2b92a58dc6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892926"
---
# <a name="parameter-nodes"></a>Węzły parametrów

W projektancie programu do cieniowania węzły parametrów reprezentują dane wejściowe programu do cieniowania, które są pod kontrolą aplikacji na podstawie na rysunku, na przykład, właściwości materiału, światła kierunkowego, położenie kamery i czasu. Ponieważ możesz zmienić te parametry, z każdym wywołaniem rysowania, można użyć tego samego programu do cieniowania, aby nadać inny wygląd obiektu.

## <a name="parameter-node-reference"></a>Węzeł odwołania do parametru

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Pozycja kamery świata**|Pozycja kamery w przestrzeni świata.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Pozycja kamery.|Brak|
|**Kierunek światła**|Wektor definiujący kierunek, w którym światła jest rzutowanie ze źródła światła w przestrzeni świata.<br /><br /> Służy to do obliczenia udziału oświetlenia i odblasków w przestrzeni świata.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do źródła światła.|Brak|
|**Otoczenie materiału**|Udział koloru rozpraszania bieżącego piksela, która jest przypisana do oświetlenia pośredniego.<br /><br /> Kolor rozpraszania piksel symuluje sposobu interakcji oświetlenia nierównej powierzchni. Otaczających materiał parametr umożliwia określenie w przybliżeniu jak wspiera oświetlenia pośredniego w wyglądzie obiektów w świecie rzeczywistym.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Kolor rozpraszania bieżącego piksela, która wynika z pośrednich — czyli otoczenia — oświetlenia.|**Dostęp**<br /> **Publiczne** Aby włączyć właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Kolor rozpraszania bieżącego piksela, która wynika z pośrednich — czyli otoczenia — oświetlenia.|
|**Rozpraszanie materiału**|Kolor, który opisuje, jak diffuses przez bieżący piksel oświetlenia bezpośredniego.<br /><br /> Kolor rozpraszania piksel symuluje sposobu interakcji oświetlenia nierównej powierzchni. Można zmienić, jak diffuses przez bieżący piksel oświetlenia bezpośredniego służy parametr rozpraszanie materiału — czyli kierunkowego punktu i reflektor.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Kolor, który opisuje, jak diffuses przez bieżący piksel oświetlenia bezpośredniego.|**Dostęp**<br /> **Publiczne** Aby włączyć właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Kolor, który opisuje, jak diffuses przez bieżący piksel oświetlenia bezpośredniego.|
|**Emisja materiału**|Udział koloru materiału bieżącego piksela, które jest przypisane do oświetlenia dostarczającego do samego siebie.<br /><br /> Służy to do symulowania świecącego obiektu; oznacza to, że obiekt, który wydziela światło. Ta światło nie ma wpływu na inne obiekty.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Udział koloru materiału bieżącego piksela, które wkrótce samodzielnie emitowanego oświetlenia.|**Dostęp**<br /> **Publiczne** Aby włączyć właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Udział koloru materiału bieżącego piksela, które wkrótce samodzielnie emitowanego oświetlenia.|
|**Odblask materiału**|Kolor opisujący Odbijanie oświetlenia bezpośredniego przez bieżącego piksela.<br /><br /> Kolor Odblaskowy piksela symuluje sposobu interakcji oświetlenia smooth, lustrzanej powierzchni. Materiał Odblaskowy parametr służy do zmiany, jak bieżący piksel oświetlenia bezpośredniego — czyli kierunkowego punktu i reflektor.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Kolor opisujący Odbijanie oświetlenia bezpośredniego przez bieżącego piksela.|**Dostęp**<br /> **Publiczne** umożliwia właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Kolor opisujący Odbijanie oświetlenia bezpośredniego przez bieżącego piksela.|
|**Moc odblasku materiału**|Wartość skalarna opisująca intensywność światła odbitego.<br /><br /> Im większy moc odblasku, bardziej intensywny i Week stają się światłem odbitym.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float`<br /> Termin wykładniczego, opisująca intensywność światła odbitego na bieżącego piksela.|**Dostęp**<br /> **Publiczne** Aby włączyć właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Wykładnik definiujący intensywność światła odbitego na bieżącego piksela.|
|**Znormalizowany czas**|Czas w sekundach, znormalizowane do zakresu [0, 1], taki sposób, że gdy jest to czas osiągnięcia 1, przywraca 0.<br /><br /> Służy to jako parametru w obliczeniach cieniowania, na przykład celu animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float`<br /> Znormalizowany czas w sekundach.|Brak|
|**czas**|Czas w sekundach.<br /><br /> Służy to jako parametru w obliczeniach cieniowania, na przykład celu animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float`<br /> Czas w sekundach.|Brak|