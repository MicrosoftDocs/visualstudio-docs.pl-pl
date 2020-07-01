---
title: Węzły parametrów
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 986b7bcc75dd39b0d41d8f614a68734a65afca0b
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768808"
---
# <a name="parameter-nodes"></a>Węzły parametrów

W projektancie programu do cieniowania węzły parametrów reprezentują dane wejściowe do cieniowania, które są pod kontrolą aplikacji, na przykład właściwości materiałowe, sygnalizatory kierunkowe, położenie kamery i czas. Ponieważ można zmienić te parametry za pomocą każdego wywołania rysowania, można użyć tego samego modułu cieniującego, aby nadać obiektowi różne wyglądy.

## <a name="parameter-node-reference"></a>Odwołanie do węzła parametru

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Pozycja świata kamery**|Pozycja kamery w przestrzeni świata.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Pozycja aparatu.|Brak|
|**Kierunek światła**|Wektor definiujący kierunek rzutowania światła ze źródła światła w przestrzeni świata.<br /><br /> Umożliwia to obliczanie oświetlenia i odblasków w przestrzeni świata.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do źródła światła.|Brak|
|**Otoczenie materiału**|Udział koloru rozpraszania bieżącego piksela, który jest przypisany do pośredniego oświetlenia.<br /><br /> Kolor rozpraszania pikseli symuluje sposób interakcji oświetlenia z niedalekimi powierzchniami. Można użyć parametru otoczenia materiału, aby przybliżyć, jak pośrednie oświetlenie przyczynia się do wyglądu obiektu w świecie rzeczywistym.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Kolor rozpraszania bieżącego piksela, który jest z powodu pośredniego, czyli otoczenia (oświetlenie).|**Dostęp**<br /> **Publiczny** , aby włączyć ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Kolor rozpraszania bieżącego piksela, który jest z powodu pośredniego, czyli otoczenia (oświetlenie).|
|**Rozpraszanie materiału**|Kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.<br /><br /> Kolor rozpraszania pikseli symuluje sposób interakcji oświetlenia z niedalekimi powierzchniami. Można użyć parametru rozpraszanie materiału, aby zmienić sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego — to znaczy, kierunkowe, punktowe i światło punktowe.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.|**Dostęp**<br /> **Publiczny** , aby włączyć ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.|
|**Emisyjny materiału**|Udział koloru bieżącego piksela, który jest przypisany do samego środka.<br /><br /> Służy do symulowania obiektu blasku. oznacza to, że obiekt dostarcza własne jasne. To światełko nie ma wpływu na inne obiekty.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Udział koloru bieżącego piksela ze względu na własne oświetlenie.|**Dostęp**<br /> **Publiczny** , aby włączyć ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Udział koloru bieżącego piksela ze względu na własne oświetlenie.|
|**Odblasków materiału**|Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.<br /><br /> Kolor odblasków piksela symuluje sposób, w jaki oświetlenie współdziała z gładkimi, podobnymi do odbicia powierzchni. Możesz użyć parametru odblasków materiału, aby zmienić sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie — to znaczy, kierunkowe, punktowe i kontrolki punktowe.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.|**Dostęp**<br /> **Publiczny** , aby zezwalać na ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.|
|**Odblasków materiału**|Wartość skalarna opisująca intensywność odblasków.<br /><br /> Im większy odblasków, tym bardziej intensywne i daleko osiągają się najważniejsze odblasków.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float`<br /> Termin wykładniczy, który opisuje intensywność odblasków świateł w bieżącym pikselu.|**Dostęp**<br /> **Publiczny** , aby włączyć ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Wykładnik, który definiuje intensywność odblasków świateł na bieżącym pikselu.|
|**Znormalizowany czas**|Czas w sekundach, znormalizowany do zakresu [0, 1], tak że gdy czas osiągnie 1, zostanie zresetowany do wartości 0.<br /><br /> Można go użyć jako parametru w obliczeniach cieniowania, na przykład w celu animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float`<br /> Znormalizowany czas (w sekundach).|Brak|
|**Godzina**|Czas (w sekundach).<br /><br /> Można go użyć jako parametru w obliczeniach cieniowania, na przykład w celu animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float`<br /> Czas (w sekundach).|Brak|