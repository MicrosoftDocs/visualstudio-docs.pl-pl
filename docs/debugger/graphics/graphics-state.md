---
title: Stan grafiki | Microsoft Docs
description: Rozwiązywanie problemów z renderowaniem przez wyświetlanie stanu grafiki dla każdego wywołania rysowania. Elementy stanu, które zmieniły się od poprzedniego wywołania są wyróżnione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c6f909d7e250be193bb446d25cd4182d4f062ebe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888605"
---
# <a name="graphics-state"></a>Stan grafiki
Okno stanu w diagnostyce grafiki programu Visual Studio pomaga zrozumieć stan grafiki, który jest aktywny w chwili obecnej zdarzenia, na przykład wywołanie rysowania.

## <a name="understanding-the-state-window"></a>Zrozumienie okna stanu
 W oknie stanu są zbierane informacje o stanie, który ma wpływ na renderowanie, i przedstawia je hierarchicznie w jednym miejscu. W zależności od wersji programu Direct3D używanej przez aplikację informacje prezentowane w oknie stanu mogą mieć różnice.

### <a name="state-views"></a>Widoki stanu
 Tabelę stanu można wyświetlić na kilka różnych sposobów:

|Widok|Opis|
|----------|-----------------|
|Widok stanu danych wejściowych interfejsu API|Ten widok przedstawia stan w podobnym układzie do obiektów Direct3D, które składają się na stan.|
|Widok stanu logicznego danych wejściowych|Ten widok przedstawia stan w widoku logicznym, który nie jest dublowany w układzie obiektów Direct3D, które tworzą stan.|
|Widok stanu przypiętego|Zamiast hierarchii, widok stanu przypiętego przedstawia przypięte elementy stanu na płaskiej liście z w pełni kwalifikowanymi nazwami. Ten widok umożliwia wyświetlenie wielu elementów stanu z różnych pakietów stanu w niewielkiej liczbie wierszy.|

##### <a name="to-change-the-state-view"></a>Aby zmienić widok stanu

- W oknie stanu w lewym górnym rogu tuż poniżej paska tytułu wybierz przycisk, który odpowiada stylowi widoku stanu, którego chcesz użyć.

  - **Pokaż widok stanu danych wejściowych interfejsu API**

  - **Pokaż widok stanu logicznego**

  - **Pokaż widok stanu przypiętego**

> [!IMPORTANT]
> Należy przypiąć stan w polu **Pokaż stan wejściowy interfejsu API** lub **pokazać widoki stanu logicznego** , aby były wyświetlane w **widoku Pokaż przypięty stan**.

### <a name="state-table-format"></a>Format tabeli stanu
 Okno stanu zawiera kilka kolumn informacji.

|Kolumna|Opis|
|------------|-----------------|
|Nazwa|Nazwa elementu stanu. Jeśli ten element reprezentuje pakiet stanu, element można rozwinąć, aby go wyświetlić.<br /><br /> W **widoku stanu wejścia interfejsu API** i Stanów **widoku stanu logicznego** , nazwy są wcięte, aby pokazać hierarchiczną relację między Stanami.<br /><br /> W stanie **widoku stanu przypięte** w pełni kwalifikowane nazwy są wyświetlane na płaskiej liście.|
|Wartość|Wartość elementu stanu.|
|Typ|Typ elementu stanu.|

### <a name="changed-state"></a>Zmieniony stan
 Stan grafiki zwykle zmienia się stopniowo między kolejnymi wywołaniami rysowania, a wiele rodzajów problemów z renderowaniem jest spowodowanych błędem zmiany stanu. Aby ułatwić znalezienie, który stan zmienił się od poprzedniego wywołania rysowania, stan, który został zmieniony, jest oznaczony gwiazdką i wyświetlany na czerwono — ma to zastosowanie nie tylko do samego stanu, ale również do jego elementu nadrzędnego stanu, aby można było łatwo sprawdzić stan zmieniony na najwyższym poziomie, a następnie przejść do szczegółów.

### <a name="pinning-state"></a>Przypinanie stanu
 Ze względu na to, że wiele aplikacji renderuje podobne obiekty sekwencyjnie, zmiana znanego zestawu stanu, czasami warto przypiąć zmiany w miejscu, aby można było zobaczyć, jak zmienia się w trakcie przenoszenia od wywołania rysowania do wywołania rysowania.

 Może to być również przydatne w przypadku izolowania źródła problemu ze względu na zmianę określonego stanu.

##### <a name="to-pin-state-in-place"></a>Aby przypiąć stan w miejscu

1. W oknie stanu Znajdź interesujący Cię stan. Może być konieczne rozszerzenie wyższego poziomu, aby znaleźć interesujące Cię szczegóły.

2. Umieść kursor nad stanem, który Cię interesuje. Ikona pinezki pojawia się po lewej stronie elementu State.

3. Wybierz ikonę pinezki, aby przypiąć element stanu na miejscu.
