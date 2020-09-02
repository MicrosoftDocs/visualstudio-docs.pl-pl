---
title: Edytuj i Kontynuuj (Visual Basic) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428564"
---
# <a name="edit-and-continue-visual-basic"></a>Edytuj i kontynuuj (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytuj i Kontynuuj to funkcja [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] debugowania, która umożliwia zmianę kodu podczas wykonywania w trybie przerwania. Po zastosowaniu zmian w kodzie można wznowić wykonywanie kodu przy użyciu nowych zmian w miejscu i zobaczyć efekt.  
  
 Możesz użyć funkcji Edytuj i Kontynuuj za każdym razem, gdy wprowadzisz tryb Break. W trybie przerwania wskaźnik instrukcji, żółta strzałka w oknie źródłowym, wskazuje wiersz, który zostanie wykonany dalej i będzie znajdował się w instrukcji wykonywalnej w obrębie metody lub treści właściwości. Można prawie dowolnie wprowadzać zmiany do instrukcji wykonywalnych w trybie przerwania, a zmiana zostanie zawarta w projekcie źródłowym. Jednak w trybie przerwania zazwyczaj nie można zmieniać instrukcji deklaracji, takich jak metody publiczne, pola publiczne lub deklaracje klas.  
  
 Po wprowadzeniu nieautoryzowanej edycji zmiana jest oznaczona przy użyciu purpurowego podkreślenia, a zadanie jest wyświetlane w Lista zadań. Jeśli chcesz kontynuować korzystanie z polecenia Edytuj i Kontynuuj, musisz cofnąć nieautoryzowaną edycję. Niektóre nieautoryzowane zmiany mogą być dozwolone, jeśli są gotowe poza Edytuj i Kontynuuj. Jeśli chcesz zachować wyniki takiej nieautoryzowanej edycji, musisz zatrzymać debugowanie i ponownie uruchomić aplikację.  
  
 Edycja i kontynuacja jest obsługiwana w przypadku projektów 64-bitowych, które są przeznaczone dla .NET Framework 4.5.1.  
  
 Polecenia Edytuj i Kontynuuj nie są obsługiwane po rozpoczęciu debugowania za pomocą **dołączania do procesu**. Polecenie Edytuj i Kontynuuj nie jest obsługiwane w przypadku zoptymalizowanego kodu, kodu zarządzanego i natywnego oraz projektów programu Compact Framework (inteligentnych urządzeń).  
  
 Tematy w tej sekcji zawierają dodatkowe informacje na temat sposobu korzystania z tej funkcji oraz tego, jakiego rodzaju zmiany są niedozwolone.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: stosowanie edycji w trybie przerwania za pomocą pleceń Edytuj i Kontynuuj](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Wyjaśnia, jak zastosować edycje kodu w trybie przerwania.  
  
 [Nieobsługiwane edycje funkcji Edytuj i kontynuuj programu Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Opisuje rodzaje edycji, które nie mogą być wykonywane w [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] Edytuj i Kontynuuj.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Edytuj i kontynuuj](../debugger/edit-and-continue.md)  
 Zawiera listę tematów dotyczących Edytuj i Kontynuuj.
