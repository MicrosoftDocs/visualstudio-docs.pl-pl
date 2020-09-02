---
title: Karta plik strony, okno dialogowe właściwości procesu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192717"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Plik stronicowania, okno dialogowe właściwości procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj karty **plik strony** , aby przejrzeć plik stronicowania procesu. Aby wyświetlić okno [dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do okna [widok procesów](../debugger/processes-view.md) . Wybierz dowolny węzeł procesu w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .  
  
 Na karcie **plik strony** dostępne są następujące ustawienia:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Bajty pliku stronicowania**|Bieżąca liczba stron, których ten proces używa w pliku stronicowania. Plik stronicowania przechowuje strony danych używanych przez proces, ale nie zawarte w innych plikach. Plik stronicowania jest używany przez wszystkie procesy, a brak miejsca w pliku stronicowania może spowodować błędy, podczas gdy inne procesy są uruchomione.|  
|**Szczytowe bajty pliku stronicowania**|Maksymalna liczba stron, których ten proces użył w pliku stronicowania.|  
|**Błędy stron**|Liczba błędów stron przez wątki wykonywane w ramach tego procesu. Błąd strony występuje, gdy wątek odwołuje się do strony pamięci wirtualnej, która nie znajduje się w jego zestawie roboczym w pamięci głównej. W związku z tym strona nie zostanie pobrana z dysku, jeśli znajduje się na liście gotowości, a tym samym już w głównej pamięci, lub jeśli jest używana przez inny proces, w którym strona jest udostępniona.|
