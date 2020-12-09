---
title: Karta Ogólne, okno dialogowe właściwości procesu | Microsoft Docs
description: Na karcie Ogólne można znaleźć informacje o procesie, w tym nazwę modułu, identyfikator procesu, priorytet podstawowy, liczbę wątków, czas procesora, czas użytkownika i czas, który upłynął.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4980437c63348050db1a007e8f541e9af9e186cc
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862740"
---
# <a name="general-tab-process-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości procesu
Skorzystaj z karty **Ogólne** , aby dowiedzieć się więcej o określonym procesie. Aby wyświetlić okno [dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do okna [widok procesów](../debugger/processes-view.md) . Wybierz dowolny węzeł procesu w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .

 Na karcie **Ogólne** dostępne są następujące ustawienia:

|Wpis|Opis|
|-----------|-----------------|
|**Nazwa modułu**|Nazwa modułu.|
|**Identyfikator procesu**|Unikatowy identyfikator tego procesu. Numery identyfikatorów procesów są ponownie używane, aby identyfikować proces tylko w okresie istnienia tego procesu. Typ obiektu procesu jest tworzony podczas uruchamiania programu. Wszystkie wątki w procesie mają tę samą przestrzeń adresową i mają dostęp do tych samych danych.|
|**Priorytet podstawowy**|Bieżący Priorytet podstawowy tego procesu. Wątki w ramach procesu mogą podnieść i obniżyć własny priorytet podstawowy względem priorytetu podstawowego procesu.|
|**Wątki**|Liczba wątków aktywnych obecnie w tym procesie.|
|**Czas procesora CPU**|Łączny czas procesora CPU poświęcony na ten proces i jego wątki. Równy czasowi użytkownika plus czas uprzywilejowany.|
|**Czas użytkownika**|Łączny czas, który upłynął, gdy wątki tego procesu poświęcają na wykonywanie kodu w trybie użytkownika w wątkach, które nie są bezczynne. Aplikacje są wykonywane w trybie użytkownika, tak jak w przypadku podsystemów, takich jak Menedżer okien i aparat grafiki.|
|**Uprzywilejowany czas**|Łączny czas, który upłynął w trybie uprzywilejowanym w nieczynnych wątkach. Warstwa usług, procedury wykonawcze i wykonywanie jądra w trybie uprzywilejowanym. Sterowniki urządzeń dla większości urządzeń oprócz kart graficznych i drukarek są również wykonywane w trybie uprzywilejowanym. Niektóre zadania, które system Windows dla aplikacji mogą pojawić się w innych procesach podsystemu, oprócz uprzywilejowanego czasu.|
|**Czas, który upłynął**|Łączny czas, który upłynął, gdy ten proces został uruchomiony.|