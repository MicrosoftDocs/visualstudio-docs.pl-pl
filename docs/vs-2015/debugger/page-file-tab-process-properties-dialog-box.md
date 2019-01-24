---
title: Karta plik stronicowania, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24fdba37be2373623d94f03e45dc5e8a41a74b84
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777605"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Plik stronicowania, okno dialogowe właściwości procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj **pliku stronicowania** kartę, aby przejrzeć plik stronicowania procesu. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **pliku stronicowania** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Bajty pliku stronicowania**|Bieżąca liczba stron, które tego procesu są używane w pliku stronicowania. Plik stronicowania przechowuje stron danych używane w procesie, ale nie jest zawarta w innych plikach. Plik stronicowania jest używany przez wszystkie procesy i braku miejsca w pliku stronicowania może powodować błędy, gdy są uruchomione inne procesy.|  
|**Szczytowe Bajty pliku stronicowania**|Maksymalna liczba stron, które ten proces został użyty w pliku stronicowania.|  
|**Błędy stron**|Liczba błędów strony w wątkach wykonywanych w ramach tego procesu. Błąd strony występuje, gdy wątek odwołuje się do strony pamięci wirtualnej, która nie znajduje się w jego zestawie roboczym w pamięci głównej. W związku z tym, strona nie zostanie pobrany z dysku jeśli znajduje się na liście gotowości i dlatego już w pamięci głównej, lub jeśli jest on używany przez inny procesu zostały udostępnione strony.|
