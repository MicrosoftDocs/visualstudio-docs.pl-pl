---
title: Karta plik stronicowania, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d45fa813a7bb75ea0cdd11a412ae35e5444883dc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924970"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Plik stronicowania, okno dialogowe właściwości procesu
Użyj **pliku stronicowania** kartę, aby przejrzeć plik stronicowania procesu. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **pliku stronicowania** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Bajty pliku stronicowania**|Bieżąca liczba stron, które tego procesu są używane w pliku stronicowania. Plik stronicowania przechowuje stron danych używane w procesie, ale nie jest zawarta w innych plikach. Plik stronicowania jest używany przez wszystkie procesy i braku miejsca w pliku stronicowania może powodować błędy, gdy są uruchomione inne procesy.|  
|**Szczytowe Bajty pliku stronicowania**|Maksymalna liczba stron, które ten proces został użyty w pliku stronicowania.|  
|**Błędy stron**|Liczba błędów strony w wątkach wykonywanych w ramach tego procesu. Błąd strony występuje, gdy wątek odwołuje się do strony pamięci wirtualnej, która nie znajduje się w jego zestawie roboczym w pamięci głównej. W związku z tym, strona nie zostanie pobrany z dysku jeśli znajduje się na liście gotowości i dlatego już w pamięci głównej, lub jeśli jest on używany przez inny procesu zostały udostępnione strony.|