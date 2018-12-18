---
title: Stan grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b45e5d922a5f2ed5a2ba15086c708c734d25e95
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476383"
---
# <a name="graphics-state"></a>Stan grafiki
Okna stanu grafiki programu Visual Studio diagnostyki pomaga w zrozumieniu stanu grafiki, który jest aktywny w momencie bieżącego zdarzenia, takie jak wywołanie rysowania.  
  
## <a name="understanding-the-state-window"></a>Opis stanu okna  
 Okno stanu zbiera razem stanie, który ma wpływ na renderowanie i przedstawia on hierarchicznie, w jednym miejscu. W zależności od używanej wersji programu Direct3D aplikacji używa, informacje wyświetlone w oknie stanu może być różnice.  
  
### <a name="state-views"></a>Widoki stanu  
 W tabeli stanu można wyświetlić na kilka różnych sposobów:  
  
|Widok|Opis|  
|----------|-----------------|  
|Widok stanu danych wejściowych interfejsu API|Ten widok przedstawia stan w układzie podobne do obiektów Direct3D wchodzące w skład stanu.|  
|Widok stanu danych wejściowych logiczne|Ten widok przedstawia stan w widoku logicznym nie dublujące układu obiektów Direct3D wchodzące w skład stanu.|  
|Przypięte widok stanu|Zamiast hierarchii Pinned widok stanu przedstawia stan przypiętych elementów jako płaską listę z w pełni kwalifikowanej nazwy. Ten widok sprawia, że jest możliwe wyświetlić wiele elementów stanu z różnych pakietów stanu w małej liczby wierszy.|  
  
##### <a name="to-change-the-state-view"></a>Aby zmienić widok stanu  
  
-   W oknie stanu w górnym lewym poniżej tytułu wybierz przycisk umożliwiająca styl widok stanu, którego chcesz użyć.  
  
    -   **Pokaż widok stanu danych wejściowych interfejsu API**  
  
    -   **Pokaż widok stanu logicznego**  
  
    -   **Pokaż widok stanu Pinned**  
  
> [!IMPORTANT]
>  Trzeba przypiąć stanu w **stanu danych wejściowych Pokaż interfejsu API** lub **stanu logicznego Pokaż** widoków dla niego będzie wyświetlana w **Pokaż przypięte widok stanu**.  
  
### <a name="state-table-format"></a>Format stan tabeli  
 Okno stanu zawiera kilka kolumn informacji.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|Nazwa|Nazwa elementu stanu. Jeśli ten element reprezentuje pakiet stanu, można rozszerzyć elementu, aby go wyświetlić.<br /><br /> W **widok stanu danych wejściowych interfejsu API** i **widok stanu logicznego** stany nazwy mają wcięcia hierarchiczną relację między stanami.<br /><br /> W **przypięty widok stanu** stanu, w pełni kwalifikowanej nazwy są wyświetlane w formie listy niezhierarchizowanej.|  
|Wartość|Wartość elementu stanu.|  
|Typ|Typ elementu stanu.|  
  
### <a name="changed-state"></a>Zmiany stanu  
 Stan grafiki zwykle zmienia przyrostowo między wywołań rysowania kolejnych i wiele rodzajów problemy z renderowaniem są spowodowane stan jest zmieniany niepoprawnie. Aby pomóc w znalezieniu, których stan zmienił się od czasu poprzedniego wywołania rysowania, stan, który jest został zmieniony oznaczone gwiazdką i wyświetlić na czerwono — dotyczy nie tylko do samego stanu, ale jego nadrzędnego stanu elementu także, dzięki czemu można łatwo dodatkowy stan zmieniony na najwyższego poziomu, a następnie przejść do szczegółów.  
  
### <a name="pinning-state"></a>Przypinanie stanu  
 Ponieważ wiele aplikacji renderowania podobne obiekty sekwencyjnie, zmiana zestawu znanego stanu, czasami jest przydatne przypiąć zmiany stanów w miejscu, dzięki czemu możesz obserwować zmiany, Przenieś z wywołania rysowania wywołanie rysowania.  
  
 Może to być również przydatne, jeśli zostały izolowane źródłem problemu się z powodu zmiany w określonym stanie.  
  
##### <a name="to-pin-state-in-place"></a>Aby przypiąć stanu w miejscu  
  
1.  W oknie Stan zlokalizować stan interesuje Cię. Może być konieczne rozwiń wyższego poziomu stanu można znaleźć szczegółowe informacje, które interesują Cię.  
  
2.  Umieść kursor na stanie, który chcesz. Ikonę pinezki pojawia się po lewej element stanu.  
  
3.  Wybierz ikonę numeru Pin, aby przypiąć element stanu w miejscu.