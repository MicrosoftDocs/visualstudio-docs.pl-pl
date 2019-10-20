---
title: Węzły parametrów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e6d90e882e40bff84898efdd20579abbfd4d309
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664143"
---
# <a name="parameter-nodes"></a>Węzły parametrów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W projektancie programu do cieniowania węzły parametrów reprezentują dane wejściowe do cieniowania, które są pod kontrolą aplikacji, na przykład właściwości materiałowe, sygnalizatory kierunkowe, położenie kamery i czas. Ponieważ można zmienić te parametry za pomocą każdego wywołania rysowania, można użyć tego samego modułu cieniującego, aby nadać obiektowi różne wyglądy.

## <a name="parameter-node-reference"></a>Odwołanie do węzła parametru

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Pozycja świata kamery**|Pozycja kamery w przestrzeni świata.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Pozycja aparatu.|Brak|
|**Kierunek światła**|Wektor definiujący kierunek rzutowania światła ze źródła światła w przestrzeni świata.<br /><br /> Umożliwia to obliczanie oświetlenia i odblasków w przestrzeni świata.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do źródła światła.|Brak|
|**Otoczenie materiału**|Udział koloru rozpraszania bieżącego piksela, który jest przypisany do pośredniego oświetlenia.<br /><br /> Kolor rozpraszania pikseli symuluje sposób interakcji oświetlenia z niedalekimi powierzchniami. Można użyć parametru otoczenia materiału, aby przybliżyć, jak pośrednie oświetlenie przyczynia się do wyglądu obiektu w świecie rzeczywistym.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Kolor rozpraszania bieżącego piksela, który jest z powodu pośredniego, czyli otoczenia (oświetlenie).|**Niego**<br /> **Publiczny** , aby włączyć ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Kolor rozpraszania bieżącego piksela, który jest z powodu pośredniego, czyli otoczenia (oświetlenie).|
|**Rozpraszanie materiału**|Kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.<br /><br /> Kolor rozpraszania pikseli symuluje sposób interakcji oświetlenia z niedalekimi powierzchniami. Można użyć parametru rozpraszanie materiału, aby zmienić sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego — to znaczy, kierunkowe, punktowe i światło punktowe.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.|**Niego**<br /> **Publiczny** , aby włączyć ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.|
|**Emisyjny materiału**|Udział koloru bieżącego piksela, który jest przypisany do samego środka.<br /><br /> Służy do symulowania obiektu blasku. oznacza to, że obiekt dostarcza własne jasne. To światełko nie ma wpływu na inne obiekty.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Udział koloru bieżącego piksela ze względu na własne oświetlenie.|**Niego**<br /> **Publiczny** , aby włączyć ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Udział koloru bieżącego piksela ze względu na własne oświetlenie.|
|**Odblasków materiału**|Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.<br /><br /> Kolor odblasków piksela symuluje sposób, w jaki oświetlenie współdziała z gładkimi, podobnymi do odbicia powierzchni. Możesz użyć parametru odblasków materiału, aby zmienić sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie — to znaczy, kierunkowe, punktowe i kontrolki punktowe.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.|**Niego**<br /> **Publiczny** , aby zezwalać na ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.|
|**Odblasków materiału**|Wartość skalarna opisująca intensywność odblasków.<br /><br /> Im większy odblasków, tym bardziej intensywne i daleko osiągają się najważniejsze odblasków.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float`<br /> Termin wykładniczy, który opisuje intensywność odblasków świateł w bieżącym pikselu.|**Niego**<br /> **Publiczny** , aby włączyć ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**<br /> Wykładnik, który definiuje intensywność odblasków świateł na bieżącym pikselu.|
|**Znormalizowany czas**|Czas w sekundach, znormalizowany do zakresu [0, 1], tak że gdy czas osiągnie 1, zostanie zresetowany do wartości 0.<br /><br /> Można go użyć jako parametru w obliczeniach cieniowania, na przykład w celu animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float`<br /> Znormalizowany czas (w sekundach).|Brak|
|**Pierwszym**|Czas (w sekundach).<br /><br /> Można go użyć jako parametru w obliczeniach cieniowania, na przykład w celu animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float`<br /> Czas (w sekundach).|Brak|
