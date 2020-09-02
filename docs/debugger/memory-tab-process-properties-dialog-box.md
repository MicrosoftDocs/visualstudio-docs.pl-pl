---
title: Karta pamięć, okno dialogowe właściwości procesu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bdfc2740094c807818922f09ca3fef0a21c9e1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62931276"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Karta Pamięć, okno dialogowe właściwości procesu
Użyj karty **pamięć** , aby zobaczyć, jak proces używa pamięci. Aby wyświetlić okno [dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do okna [widok procesów](../debugger/processes-view.md) . Wybierz dowolny węzeł procesu w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .

 Na karcie **pamięć** dostępne są następujące ustawienia:

|Wpis|Opis|
|-----------|-----------------|
|**Bajty wirtualne**|Bieżący rozmiar (w bajtach) wirtualnej przestrzeni adresowej używanej przez proces. Użycie wirtualnej przestrzeni adresowej nie musi oznaczać odpowiedniego użycia obu stron dysku lub pamięci głównej. Jednak miejsce wirtualne jest ograniczone i użycie zbyt dużej liczby może ograniczyć możliwość ładowania bibliotek przez proces.|
|**Szczytowe Bajty wirtualne**|Maksymalna liczba bajtów wirtualnej przestrzeni adresowej używanej w dowolnym momencie przez proces.|
|**Zestaw roboczy**|Zestaw stron pamięci, które zostały ostatnio zmienione przez wątki w procesie. Jeśli ilość wolnej pamięci w komputerze jest większa niż wartość progowa, strony są pozostawiane w zestawie roboczym procesu, nawet jeśli nie są używane. Gdy wolna pamięć spadnie poniżej wartości progowej, strony są przycinane z zestawu roboczego. Jeśli są one wymagane, zostaną one przywrócone do zestawu roboczego przed opuszczeniem pamięci głównej.|
|**Szczytowy zestaw roboczy**|Maksymalna liczba stron w zestawie roboczym tego procesu w dowolnym momencie.|
|**Bajty puli stronicowanej**|Bieżąca ilość stronicowanej puli, która została przypisana przez proces. Pula stronicowana to obszar pamięci systemowej, w którym składniki systemu operacyjnego uzyskują miejsce w miarę wykonywania wyznaczonych zadań. Strony puli stronicowanej mogą być stronicowane do pliku stronicowania, gdy system nie uzyskuje do niego dostępu przez dłuższy czas.|
|**Bajty puli niestronicowanej**|Bieżąca liczba bajtów w puli niestronicowanej przydzielonej przez proces. Pula niestronicowana to obszar pamięci systemowej, w którym składniki systemu operacyjnego są uzyskiwane w ramach wyznaczonych zadań. Strony puli niestronicowanej nie mogą być stronicowane do pliku stronicowania; pozostaną one w pamięci głównej, o ile są przydzieleni.|
|**Bajty prywatne**|Bieżąca liczba bajtów przydzielonych przez ten proces, które nie mogą być współużytkowane z innymi procesami.|
|**Wolne bajty**|Całkowita nieużywana wirtualna przestrzeń adresowa tego procesu.|
|**Bajty zarezerwowane**|Całkowita ilość pamięci wirtualnej zarezerwowanej do użytku w przyszłości przez ten proces.|
|**Wolne bajty obrazu**|Ilość wirtualnej przestrzeni adresowej, która nie jest używana ani zastrzeżona przez obrazy w ramach tego procesu.|
|**Zarezerwowane bajty obrazu**|Suma wszystkich pamięci wirtualnych zarezerwowanych przez obrazy działające w ramach tego procesu.|