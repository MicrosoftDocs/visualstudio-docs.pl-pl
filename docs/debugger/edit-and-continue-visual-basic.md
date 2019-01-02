---
title: Edytuj i Kontynuuj (Visual Basic) | Dokumentacja firmy Microsoft
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3e1305a67fa4347a8b39b677c5be31ada257b65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838024"
---
# <a name="edit-and-continue-visual-basic"></a>Edytuj i kontynuuj (Visual Basic)
Edytuj i Kontynuuj jest funkcją, aby uzyskać [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] debugowania, która umożliwia zmianę kodu, podczas wykonywania w trybie przerwania. Po zastosowaniu edycji kodu można wznowić wykonywania kodu za pomocą nowego edycji w miejscu i zobaczyć efekt.  
  
 Możesz użyć edycji i kontynuowania funkcji zawsze wtedy, gdy tryb przerwania. W trybie przerwania, wskaźnika instrukcji, żółty grot strzałki w oknie źródłowym wskazuje na wiersz zawierający instrukcji wykonywalnej w treści metody lub właściwości, który ma być wykonany dalej.

 Edytuj i Kontynuuj obsługuje większość zmian, które można wprowadzić podczas sesji debugowania, ale istnieją pewne wyjątki. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).   
  
 Po wprowadzeniu nieautoryzowane zmiany, zmiana jest oznaczona za pomocą purpurowy falistą i zadaniem jest wyświetlana na liście zadań. Jeśli chcesz nadal korzystać, Edytuj i Kontynuuj, musisz cofnąć nieautoryzowane zmiany. Może być dozwolony nieautoryzowanych zmian, jeśli będą wykonywane poza Edytuj i Kontynuuj. Jeśli chcesz zachować wyniki nieautoryzowanych edycji, należy zatrzymać debugowanie i ponownie uruchom aplikację.  
  
 Edytuj i Kontynuuj jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows dla systemu Windows 10 i x86 i x64 aplikacji, przeznaczonych dla platformy .NET Framework 4.6 pulpitu lub nowszej wersji (.NET Framework jest tylko wersja desktop).

 > [!NOTE]
 > Platform i nieobsługiwanych aplikacji obejmują platformy ASP.NET 5, Silverlight 5 i Windows 8.1.
  
 Edytuj i Kontynuuj nie jest obsługiwana podczas uruchamiania debugowania przy użyciu **dołączyć do procesu**. Edytuj i Kontynuuj nie jest obsługiwane dla zoptymalizowanego kodu lub mieszane kodu zarządzanego i natywnego. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).
  
 Tematy w tej sekcji zawierają dodatkowe szczegóły dotyczące sposobu używania tej funkcji i jakiego rodzaju zmiany są niedozwolone.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Zastosowanie zmian w trybie przerwania za pomocą Edytuj i Kontynuuj](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Wyjaśnia sposób stosowania zmian kodu w trybie przerwania.  
  
 [Obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md)   
 W tym artykule opisano, jakie typy zmian nie mogą być wykonywane w [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] Edytuj i Kontynuuj.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Edytuj i kontynuuj](../debugger/edit-and-continue.md)  
 Zawiera listę tematów na Edytuj i Kontynuuj.
