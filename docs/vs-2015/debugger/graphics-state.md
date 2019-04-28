---
title: Stan grafiki | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe97461800d6f6e6eb285dd7eddb610ab2f5b5ac
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420067"
---
# <a name="graphics-state"></a>Stan grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okna stanu grafiki programu Visual Studio diagnostyki ułatwia zrozumienie stanu grafiki, który jest aktywny w momencie bieżącego zdarzenia, takie jak wywołania rysowania.  
  
## <a name="understanding-the-state-window"></a>Omówienie okna stanu  
 W oknie stanu zbiera dane ze sobą stanu który ma wpływ na renderowania i prezentuje hierarchiczny, w tym miejscu. W zależności od używanej wersji programu Direct3D aplikacja używa, informacje znajdujące się w oknie stanu może być różnice.  
  
### <a name="state-views"></a>Widoki stanów  
 Tabela stanu można wyświetlić na kilka różnych sposobów:  
  
|Widok|Opis|  
|----------|-----------------|  
|Widok stanu danych wejściowych interfejsu API|Ten widok przedstawia stan w układu podobnego do obiekty Direct3D, które tworzą stan.|  
|Widok logiczny stanu danych wejściowych|Ten widok przedstawia stan, w widoku logicznym odpowiadającej nie układ obiekty Direct3D, które tworzą stan.|  
|Przypięte widok stanu|Zamiast hierarchii Pinned widok stanu przedstawia stan przypięte elementy w formie płaskiej listy przy użyciu w pełni kwalifikowanej nazwy. Ten widok sprawia, że istnieje możliwość wyświetlania stanu elementów z różnych pakietów stanu w małej liczby wierszy.|  
  
##### <a name="to-change-the-state-view"></a>Aby zmienić widok stanu  
  
- W oknie stanu w prawym górnym lewym tuż poniżej tytułu wybierz przycisk, który odpowiada styl widoku stanu, którego chcesz użyć.  
  
    - **Pokaż widok stanu danych wejściowych interfejsu API**  
  
    - **Pokaż widok stanu logicznego**  
  
    - **Pokaż widok stanu Pinned**  
  
> [!IMPORTANT]
> Trzeba przypiąć stanu w **Pokaż interfejsu API danych wejściowych w stanie** lub **stanu logicznego Pokaż** widoków dla niego będzie wyświetlana w **Pokaż przypięte widok stanu**.  
  
### <a name="state-table-format"></a>Format tabeli stanu  
 W oknie stanu przedstawia kilka kolumn informacji.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|Nazwa|Nazwa elementu stanu. Jeśli ten element reprezentuje pakiet, stanu, można rozszerzyć element, aby go wyświetlić.<br /><br /> W **interfejsu API danych wejściowych w widoku stanu** i **widok stanu logicznego** stany, nazwy mają wcięcia hierarchiczną relację między stanami.<br /><br /> W **przypięte widok stanu** stanu, w pełni kwalifikowanej nazwy są wyświetlane w formie płaskiej listy.|  
|Wartość|Wartość elementu stanu.|  
|Typ|Typ elementu stanu.|  
  
### <a name="changed-state"></a>Zmiana stanu  
 Stan grafiki zazwyczaj zmienia się stopniowo między wywołaniami rysowania kolejnej i wiele rodzajów problemów z renderowaniem powstają, gdy stan jest zmieniany niepoprawnie. Aby pomóc w znalezieniu, których stan zmienił się od poprzedniego wywołania rysowania, stan, który jest został zmieniony jest oznaczone gwiazdką i wyświetlane na czerwono — dotyczy to nie tylko sam stan, ale jego nadrzędnego stan elementu, dzięki czemu możesz w prosty sposób obserwować zmiany stanu na najwyższego poziomu, a następnie przejść do szczegółów.  
  
### <a name="pinning-state"></a>Stan przypinania  
 Ponieważ wiele aplikacji renderowania podobne obiekty sekwencyjnie, zmieniając znanego zestawu stanu, czasami jest przydatne przypiąć zmiany stanów w miejscu, aby obejrzeć, jak zmienia się przenieść z wywołania rysowania wywołania rysowania.  
  
 Może to być również przydatne, jeśli został izolowany źródłem problemu się z powodu zmiany w określonym stanie.  
  
##### <a name="to-pin-state-in-place"></a>Aby przypiąć stanu w miejscu  
  
1. W oknie stanu odszukaj stan, który chcesz wziąć. Może być konieczne rozwiń wyższego poziomu stanu, aby znaleźć szczegółowe informacje, których interesuje Cię.  
  
2. Umieść kursor nad stan, który chcesz wziąć. Ikona przypinania pojawia się po lewej stronie element stanu.  
  
3. Wybierz ikonę pinezki, aby przypiąć element stanu w miejscu.
