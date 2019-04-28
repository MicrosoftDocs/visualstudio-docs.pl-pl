---
title: Karta przestrzeń, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 563d54c39b4d9ce3bb2d76a9e531161c2c4ee5b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929818"
---
# <a name="space-tab-process-properties-dialog-box"></a>Karta Przestrzeń, okno dialogowe właściwości procesu
Użyj **miejsca** kartę do zbadania przestrzeni adresowej procesu. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz **właściwości** z **widoku** menu.

 Następujące ustawienia są dostępne na **miejsca** karty:

|Wpis|Opis|
|-----------|-----------------|
|**Pokaż dla przestrzeni oznaczonej jako**|Użyj tego pola listy, aby wybrać kategorię miejsca (obraz, mapowana, zastrzeżone lub nieprzypisane).|
|**Bajty wykonywalne**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej używanej przez ten proces. Pamięć pliku wykonywalnego jest pamięci, które mogą być wykonywane przez programy, ale może nie być odczytu lub zapisu.|
|**Exec — tylko do odczytu w bajtach**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej używany przy użyciu właściwości tylko do odczytu, które są używane przez ten proces. Exec — tylko do odczytu pamięci jest pamięcią, która może być wykonane, a także odczytu.|
|**Exec odczyt / zapis bajtów**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej używany przy użyciu właściwości odczytu / zapisu, które używa tego procesu. Exec — odczytu i zapisu pamięci jest pamięci, która jest wykonywana przez programy, a także do odczytu i modyfikować.|
|**Exec — zapis bajtów kopiowania**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej, które można wykonać przez programy, a także odczytywać i zapisywać. Ten typ ochrony jest używany, gdy pamięci musi być współużytkowane między procesami. Jeśli procesy do udostępniania tylko do odczytu pamięci, następnie wszystkie używają tej samej pamięci. Jeśli proces współużytkujący żąda dostępu do zapisu, kopia tej pamięci zostaną wprowadzone dla procesu.|
|**Bajty niedostępne**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej procesu uniemożliwia używanie go. Naruszenie zasad dostępu jest generowany, gdy zapisu lub odczytu zostanie podjęta.|
|**Tylko do odczytu w bajtach**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej, które mogą być wykonywane, a także odczytu.|
|**Bajty odczytu / zapisu**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej, która umożliwia odczytywanie i zapisywanie.|
|**Zapis / kopia bajtów**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej, która umożliwia udostępnianie pamięci, do odczytu, ale nie do zapisu. Procesy odczytują tę pamięć, mogą współużytkować ten sam pamięci. Jednak gdy procesy chce mieć odczyt/zapis dostęp do tej pamięci współużytkowanej, kopię pamięci składa się do zapisu.|