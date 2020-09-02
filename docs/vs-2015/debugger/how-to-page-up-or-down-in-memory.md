---
title: 'Instrukcje: stronicowanie w górę lub w dół w pamięci | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc05772e6376dbe151d5ca71b9ee221e61a7be88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157854"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Porady: stronicowanie w górę lub w dół w pamięci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas wyświetlania zawartości pamięci w oknie **pamięci** lub w oknie **demontażu** można użyć pionowego paska przewijania, aby przenieść w górę lub w dół w obszarze pamięci.  
  
### <a name="to-page-up-or-down-in-memory"></a>Na stronę w górę lub w dół w pamięci  
  
1. Na stronę w dół (przejdź do wyższego adresu pamięci) kliknij pionowy pasek przewijania poniżej pola przewijania.  
  
2. Aby Page Up (przenieść na niższy adres pamięci), kliknij pionowy pasek przewijania powyżej przycisku przewijania.  
  
   Zauważ również, że pionowy pasek przewijania działa w sposób niestandardowym. Przestrzeń adresowa nowoczesnego komputera jest bardzo duża i będzie można ją łatwo stracić, pobierając kciuk paska przewijania i przeciągając go do lokalizacji losowej. Z tego powodu kciuk jest "springloaded" i zawsze pozostaje w środku paska przewijania. W aplikacjach kodu natywnego można wyłączać się w górę lub w dół, ale nie można przewijać w dowolny sposób.  
  
   W aplikacjach zarządzanych rozzbiór jest ograniczony do jednej funkcji i można go przewinąć w normalny sposób.  
  
   Zobaczysz, że wyższe adresy są wyświetlane u dołu okna. Aby wyświetlić wyższy adres, należy przenieść w dół, a nie w górę.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>Aby przenieść jedną instrukcję w górę lub w dół  
  
- Kliknij strzałkę u góry lub u dołu pionowego paska przewijania.  
  
## <a name="see-also"></a>Zobacz też  
 [Okna pamięci](../debugger/memory-windows.md)   
 [Instrukcje: korzystanie z okna demontażu](../debugger/how-to-use-the-disassembly-window.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
