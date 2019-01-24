---
title: Edytuj i Kontynuuj (Visual Basic) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24782fee98cff09513ff2b4d1606f2be0bd9fbd2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795034"
---
# <a name="edit-and-continue-visual-basic"></a>Edytuj i kontynuuj (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytuj i Kontynuuj jest funkcją, aby uzyskać [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] debugowania, która umożliwia zmianę kodu, podczas wykonywania w trybie przerwania. Po zastosowaniu edycji kodu można wznowić wykonywania kodu za pomocą nowego edycji w miejscu i zobaczyć efekt.  
  
 Możesz użyć edycji i kontynuowania funkcji zawsze wtedy, gdy tryb przerwania. W trybie przerwania, wskaźnika instrukcji, żółty grot strzałki w oknie źródła wskazuje na wierszu, który zostanie wykonany obok i będą znajdować się w instrukcji wykonywalnej w treści metody lub właściwości. Możesz wprowadzić niemal każdego rodzaju zmiany instrukcji wykonywalnych w trybie przerwania, a zmiany zostaną uwzględnione w podstawowej projektu. W trybie przerwania, jednak ogólnie nie możesz zmienić instrukcje deklaracji, takich jak metody publiczne, pola publiczne lub deklaracji klasy.  
  
 Po wprowadzeniu nieautoryzowane zmiany, zmiana jest oznaczona za pomocą purpurowy falistą i zadaniem jest wyświetlana na liście zadań. Jeśli chcesz nadal korzystać, Edytuj i Kontynuuj, musisz cofnąć nieautoryzowane zmiany. Może być dozwolony nieautoryzowanych zmian, jeśli będą wykonywane poza Edytuj i Kontynuuj. Jeśli chcesz zachować wyniki nieautoryzowanych edycji, należy zatrzymać debugowanie i ponownie uruchom aplikację.  
  
 Edytuj i Kontynuuj jest obsługiwana dla projektów 64-bitowych, przeznaczonych dla programu .NET Framework 4.5.1.  
  
 Edytuj i Kontynuuj nie jest obsługiwana podczas uruchamiania debugowania przy użyciu **dołączyć do procesu**. Edytuj i Kontynuuj nie jest obsługiwane dla zoptymalizowanego kodu, kod mieszany zarządzanego i natywnego lub projektów Compact Framework (urządzenia przenośne).  
  
 Tematy w tej sekcji zawierają dodatkowe szczegóły dotyczące sposobu używania tej funkcji i jakiego rodzaju zmiany są niedozwolone.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Stosowanie edycji w trybie przerwania za pomocą funkcji Edytuj i kontynuuj](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Wyjaśnia sposób stosowania zmian kodu w trybie przerwania.  
  
 [Nieobsługiwane edycje funkcji Edytuj i kontynuuj programu Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 W tym artykule opisano, jakie typy zmian nie mogą być wykonywane w [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] Edytuj i Kontynuuj.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Edytuj i kontynuuj](../debugger/edit-and-continue.md)  
 Zawiera listę tematów na Edytuj i Kontynuuj.
