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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b762fc95d510d5b99a2d4f8f939ef1801b5e70cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891569"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Plik stronicowania, okno dialogowe właściwości procesu
Użyj karty **plik strony** , aby przejrzeć plik stronicowania procesu. Aby wyświetlić okno [dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do okna [widok procesów](../debugger/processes-view.md) . Wybierz dowolny węzeł procesu w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .

 Na karcie **plik strony** dostępne są następujące ustawienia:

|Wpis|Opis|
|-----------|-----------------|
|**Bajty pliku stronicowania**|Bieżąca liczba stron, których ten proces używa w pliku stronicowania. Plik stronicowania przechowuje strony danych używanych przez proces, ale nie zawarte w innych plikach. Plik stronicowania jest używany przez wszystkie procesy, a brak miejsca w pliku stronicowania może spowodować błędy, podczas gdy inne procesy są uruchomione.|
|**Szczytowe bajty pliku stronicowania**|Maksymalna liczba stron, których ten proces użył w pliku stronicowania.|
|**Błędy stron**|Liczba błędów stron przez wątki wykonywane w ramach tego procesu. Błąd strony występuje, gdy wątek odwołuje się do strony pamięci wirtualnej, która nie znajduje się w jego zestawie roboczym w pamięci głównej. W związku z tym strona nie zostanie pobrana z dysku, jeśli znajduje się na liście gotowości, a tym samym już w głównej pamięci, lub jeśli jest używana przez inny proces, w którym strona jest udostępniona.|