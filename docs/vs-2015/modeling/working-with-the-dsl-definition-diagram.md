---
title: Praca z diagramem definicji DSL | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd4b15fb7c0f1cbc0630779ecef0373977bb2056
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694222"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Praca z diagramem definicji DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagram [!INCLUDE[dsl](../includes/dsl-md.md)] definicja jest ważnym narzędziem do definiowania języka specyficznego dla domeny. Możesz dodać elementy do domeny, modelowanie i definiowanie relacji na diagramie, a także mogą modyfikować układ diagramu, aby był bardziej czytelny.  
  
## <a name="the-layout-of-the-diagram"></a>Układ diagramu  
 [!INCLUDE[dsl](../includes/dsl-md.md)] Diagram definicja ma dwie partycje **klasy i relacje** partycji i **elementów diagramu** partycji. **Klasy i relacje** partycji zawiera klasami domeny i relacje domeny oraz dziedziczenia. **Elementów diagramu** partycji Wyświetla kształt klasy, klasy łącznika, toru klasy i wygenerowanego diagramu projektanta.  
  
 Klasy domeny mogą być wyświetlane w wielu lokalizacjach **klasy i relacje** partycji. Definicja klasy domeny Wyświetla drzewo dziedziczenia, jeśli jest klasę bazową dla innych klas domeny i drzewa relacji, jeśli jest źródło relacji osadzania lub odwołanie. Symbole zastępcze klasy domeny są wyświetlane jako elementy docelowe relacji osadzania lub odwołania. Domyślnie, symbol zastępczy elementy są wyświetlane z **właściwości domeny** przedziału zwinięte. Dziedziczenie lub relacji osadzania lub odwołania nie są widoczne.  
  
 Po dodaniu klasy domeny, pojawia się w dolnej części **klasy i relacje** partycji. Po dodaniu, osadzania lub odwoływać się do relacji, jej rysowania w obszarze i na prawo od klasy domeny źródłowej.  
  
 W miarę dodawania relacji i klas domeny, może stać się trudne do zlokalizowania klasy określonej domeny. Klasy domeny można znaleźć, klikając prawym przyciskiem myszy w **Eksplorator DSL** , a następnie klikając polecenie **zlokalizuj w diagramie**.  
  
 W poniższych sekcjach opisano, jak zmienić wygląd diagramu, aby ułatwić interpretowanie.  
  
## <a name="copying-elements"></a>Kopiowanie elementów  
 Można użyć kopii, wyciąć i wkleić elementy diagramem definicji DSL.  
  
## <a name="zooming-in-or-out-on-the-diagram"></a>Powiększanie lub pomniejszanie na diagramie  
 Można powiększyć lub na diagramie, za pomocą **projektanta DSL** narzędzi, aby ustawić poziom powiększenia.  
  
## <a name="hiding-map-lines"></a>Ukrywanie linie mapy  
 Linie mapy są wiersze, które są rysowane między klasą domeny lub relacji domeny i kształtu lub łącznik, z którą jest zamapowany. Linie mapy można ukryć, klikając **Pokaż linie mapy** znajdujący się na **projektanta DSL** paska narzędzi. Pokaż wiersze, kliknij ponownie przycisk.  
  
## <a name="changing-the-diagram-layout"></a>Zmienianie układu diagramu  
 Można zmienić układ **klasy i relacje** partycji w następujący sposób.  
  
### <a name="expandcollapse"></a>Rozwiń/Zwiń  
 Można zmniejszyć rozmiar elementu kształt przedziału, który reprezentuje klasę domeny lub kształtu go prawym przyciskiem myszy, a następnie klikając polecenie **Zwiń**. Spowoduje to ukrycie **właściwości domeny** przedział kształtu. Aby wyświetlić **właściwości domeny** przedział ponownie, kliknij prawym przyciskiem myszy kształt, a następnie kliknij przycisk **rozwiń**.  
  
### <a name="move-updown"></a>Przenieś w górę/w dół  
 W partycji można przenieść domeny klasy lub diagramie element w górę lub w dół, kliknij prawym przyciskiem myszy element, a następnie klikając polecenie **Przenieś w górę** lub **Przenieś w dół**. Jeśli przenosisz element zastępczy, który jest wyświetlany jako element docelowy relacji osadzania lub odwołania, relacji będzie przenoszą się z nim.  
  
### <a name="expandcollapse-relationships-tree"></a>Rozwiń/Zwiń drzewo relacji  
 Klasa domeny roli źródłowej jest odtwarzany w relacji osadzania lub odwołania z innych klas domeny, możesz ukryć relacje kliknij prawym przyciskiem myszy definicji klasy domeny, a następnie klikając polecenie **drzewa relacji Zwiń**. Aby wyświetlić zależności, kliknij prawym przyciskiem myszy element definicji, a następnie kliknij przycisk **rozwiń drzewo relacji**.  
  
### <a name="expandcollapse-inheritance-tree"></a>Rozwiń/Zwiń drzewo dziedziczenia  
 Klasy domeny jest klasą podstawową innych klas domeny, możesz ukryć drzewo dziedziczenia kliknij prawym przyciskiem myszy definicji klasy domeny, a następnie klikając polecenie **Zwiń drzewo dziedziczenia**. Aby wyświetlić drzewo dziedziczenia, kliknij prawym przyciskiem myszy element definicji, a następnie kliknij przycisk **rozwiń drzewo dziedziczenia**.  
  
### <a name="bring-tree-here"></a>Wyświetl drzewo tutaj  
 Można konsolidować diagramu, kliknij prawym przyciskiem myszy klasę domeny symbol zastępczy, a następnie klikając polecenie **przenieść drzewa w tym miejscu**. Klasa domeny symbolu zastępczego staje się element definicji i wyświetla dziedziczenie i relacje drzewa. Element definicji poprzedniej wersji portalu staje się element zastępczy, jeśli jest to element docelowy relacji lub obiekt podrzędny w relacji dziedziczenia; w przeciwnym razie zniknie.  
  
### <a name="split-tree"></a>Podziel drzewo  
 Możesz rozbić drzewa dziedziczenia lub relacje kliknij prawym przyciskiem myszy definicji klasy domeny, który wyświetla je, a następnie klikając polecenie **Podziel drzewo**. Element definicji staje się elementem symbolu zastępczego i definicji klasy domeny, wraz z jego dziedziczenia i drzewa relacji, zostanie wyświetlony u dołu tej partycji.  
  
### <a name="show-as-class"></a>Pokaż jako klasę  
 Jeśli relacji domeny ma relacje, lub ma relacji osadzania lub odwołania z innych relacji domeny, można wyświetlić relację jako klasę, kliknij prawym przyciskiem myszy relację, a następnie klikając polecenie **Pokaż jako klasę** . Relacja będzie wyświetlane z **właściwości domeny** przedziałów i pokaże drzew dziedziczenie i relacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
