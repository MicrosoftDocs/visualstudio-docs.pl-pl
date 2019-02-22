---
title: Karta klasa, okno dialogowe właściwości | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0917c9a038b42e6302ec1f1782f095ca397a92ef
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628354"
---
# <a name="class-tab-window-properties-dialog-box"></a>Karta Klasa, okno dialogowe właściwości okna
Użyj **klasy** kartę, aby wyświetlić informacje dotyczące klasy wybranego okna. Aby wyświetlić [okno dialogowe właściwości](../debugger/window-properties-dialog-box.md), Przenieś fokus do [widoku Windows](../debugger/windows-view.md) okna. Zaznacz dowolny węzeł okna w drzewie, a następnie wybierz **właściwości** z **widoku** menu.

 Następujące ustawienia są dostępne na **klasy** karty:

|Wpis|Opis|
|-----------|-----------------|
|**Nazwa klasy**|Nazwa (lub liczbę porządkową) tej klasy okna.|
|**Style klasy**|Kombinacja kody stylu klasy.|
|**Bajty klasy**|Dane aplikacji skojarzonych z tą klasą okna.|
|**Atom klasy**|Atom klasy zwrócony przez **RegisterClass** wywołania.|
|**Dojście wystąpienia**|Dojście wystąpienia modułu, który zarejestrował klasy. Uchwyty wystąpienia nie są unikatowe.|
|**Bajty okna**|Liczba bajtów dodatkowej skojarzony z oknem każdej tej klasy. Znaczenie tych bajtów jest określany przez aplikację. Rozwiń pole listy, aby wyświetlić wartości bajtów w formacie typu DWORD.|
|**Proces okna**|Bieżący adres **WndProc** funkcji dla systemu windows tej klasy. To różni się od **proces okna** na **ogólne** kartę, jeśli okno jest podklasą klasy.|
|**Nazwy menu**|Nazwa menu głównego, skojarzony z systemem windows tej klasy ("none" w przypadku menu nie).|
|**Uchwyt ikony**|Uchwyt ikony, która jest skojarzona z systemem windows tej klasy ("none" w przypadku żadnej ikony).|
|**Uchwyt kursora**|Dojście do kursora, który jest skojarzony z systemem windows tej klasy ("none" w przypadku brak kursora).|
|**Pędzel**|Dojście do pędzel tła, skojarzony z systemem windows w tej klasie lub jednego z wstępnie zdefiniowanych kolorów COLOR_ * za malowanie tło okna, ("none" w przypadku brak pędzla).|