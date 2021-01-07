---
title: Karta plik strony, okno dialogowe właściwości procesu | Microsoft Docs
description: Użyj karty plik strony właściwości procesu, aby przejrzeć plik stronicowania procesu. W tym artykule opisano dostępne ustawienia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47f4a2e9215cb2e98fdfefecdf978cb4a442ad84
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975059"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Plik stronicowania, okno dialogowe właściwości procesu
Użyj karty **plik strony** , aby przejrzeć plik stronicowania procesu. Aby wyświetlić okno [dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do okna [widok procesów](../debugger/processes-view.md) . Wybierz dowolny węzeł procesu w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .

 Na karcie **plik strony** dostępne są następujące ustawienia:

|Wpis|Opis|
|-----------|-----------------|
|**Bajty pliku stronicowania**|Bieżąca liczba stron, których ten proces używa w pliku stronicowania. Plik stronicowania przechowuje strony danych używanych przez proces, ale nie zawarte w innych plikach. Plik stronicowania jest używany przez wszystkie procesy, a brak miejsca w pliku stronicowania może spowodować błędy, podczas gdy inne procesy są uruchomione.|
|**Szczytowe bajty pliku stronicowania**|Maksymalna liczba stron, których ten proces użył w pliku stronicowania.|
|**Błędy stron**|Liczba błędów stron przez wątki wykonywane w ramach tego procesu. Błąd strony występuje, gdy wątek odwołuje się do strony pamięci wirtualnej, która nie znajduje się w jego zestawie roboczym w pamięci głównej. W związku z tym strona nie zostanie pobrana z dysku, jeśli znajduje się na liście gotowości, a tym samym już w głównej pamięci, lub jeśli jest używana przez inny proces, w którym strona jest udostępniona.|