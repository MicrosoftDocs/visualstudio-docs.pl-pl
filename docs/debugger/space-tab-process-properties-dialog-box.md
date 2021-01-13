---
title: Karta przestrzeń, okno dialogowe właściwości procesu | Microsoft Docs
description: Dowiedz się, jak wyświetlić okno dialogowe właściwości procesu w programie Spy + + podczas debugowania. Zapoznaj się z ustawieniami dostępnymi na karcie Space.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe168f34baf65b00eab59e94afb30e07dfe89b50
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149082"
---
# <a name="space-tab-process-properties-dialog-box"></a>Karta Przestrzeń, okno dialogowe właściwości procesu
Użyj zakładki **Space (miejsce** ), aby przeanalizować przestrzeń adresową procesu. Aby wyświetlić okno [dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do okna [widok procesów](../debugger/processes-view.md) . Wybierz dowolny węzeł procesu w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .

 Na karcie **Space (miejsce** ) dostępne są następujące ustawienia:

|Wpis|Opis|
|-----------|-----------------|
|**Pokaż dla przestrzeni oznaczonej jako**|Użyj tego pola listy, aby wybrać kategorię miejsca (obraz, zamapowane, zarezerwowane lub nieprzypisane).|
|**Bajty wykonywalne**|Dla wybranej kategorii suma całej przestrzeni adresowej używanej przez ten proces. Pamięć wykonywalna jest pamięcią, która może być wykonywana przez programy, ale nie może być odczytywana ani zapisywana.|
|**Wykonywalne bajty tylko do odczytu**|Dla wybranej kategorii suma całej używanej przestrzeni adresowej z właściwościami tylko do odczytu, które są używane przez ten proces. Pamięć exec-tylko do odczytu jest pamięcią, którą można wykonać, a także odczytać.|
|**Bajty wykonywalne odczytu i zapisu**|Dla wybranej kategorii suma całej używanej przestrzeni adresowej z właściwościami odczytu i zapisu, które są używane przez ten proces. Pamięć exec do odczytu i zapisu jest pamięcią, która może być wykonywana przez programy, a także odczytywane i modyfikowane.|
|**Bajty kopii wykonywalnych i zapisu**|Dla wybranej kategorii suma wszystkich przestrzeni adresowej, które mogą być wykonywane przez programy, a także odczyt i zapis. Ten typ ochrony jest używany, gdy pamięć musi być współdzielona między procesami. Jeśli proces udostępniania tylko odczytaje pamięć, wszystkie będą używać tej samej pamięci. Jeśli proces udostępniania żąda dostępu do zapisu, zostanie przeprowadzona kopia tej pamięci dla tego procesu.|
|**Bajty bez dostępu**|Dla wybranej kategorii suma wszystkich przestrzeni adresowej, która uniemożliwia procesowi korzystanie z niego. Jest generowane naruszenie zasad dostępu w przypadku próby zapisu lub odczytu.|
|**Bajty tylko do odczytu**|Dla wybranej kategorii suma wszystkich przestrzeni adresowej, które można wykonać, a także odczytać.|
|**Bajty odczytu i zapisu**|Dla wybranej kategorii suma wszystkich przestrzeni adresowej, która umożliwia odczytywanie i zapisywanie.|
|**Bajty zapisu i kopiowania**|Dla wybranej kategorii suma wszystkich przestrzeni adresowej, która umożliwia udostępnianie pamięci do odczytu, ale nie do zapisu. Gdy procesy odczytują tę pamięć, mogą współużytkować tę samą pamięć. Jednak gdy proces udostępniania chce mieć dostęp do odczytu i zapisu do tej pamięci współdzielonej, kopia tej pamięci jest wykonywana do zapisu.|