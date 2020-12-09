---
title: Edytuj i Kontynuuj (Visual Basic) | Microsoft Docs
description: Edycja i kontynuacja jest dostępna dla projektów Visual Basic. Dowiedz się, jakie zmiany są obsługiwane i jak można kontrolować, czy są stosowane zmiany.
ms.custom: SEO-VS-2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4560973cd6ccd2bbfee48028494731935945a4c
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862974"
---
# <a name="edit-and-continue-visual-basic"></a>Edytuj i kontynuuj (Visual Basic)
Edytuj i Kontynuuj to funkcja [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] debugowania, która umożliwia zmianę kodu podczas wykonywania w trybie przerwania. Po zastosowaniu zmian w kodzie można wznowić wykonywanie kodu przy użyciu nowych zmian w miejscu i zobaczyć efekt.

 Możesz użyć funkcji Edytuj i Kontynuuj za każdym razem, gdy wprowadzisz tryb Break. W trybie przerwania wskaźnik instrukcji, żółta strzałka w oknie źródło, wskazuje wiersz zawierający instrukcję wykonywalną w metodzie lub treści właściwości, która zostanie wykonana dalej.

 Polecenie Edytuj i Kontynuuj obsługuje większość zmian, które mogą zostać wprowadzone podczas sesji debugowania, ale istnieją pewne wyjątki. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Po wprowadzeniu nieautoryzowanej edycji zmiana jest oznaczona przy użyciu purpurowego podkreślenia, a zadanie jest wyświetlane w Lista zadań. Jeśli chcesz kontynuować korzystanie z polecenia Edytuj i Kontynuuj, musisz cofnąć nieautoryzowaną edycję. Niektóre nieautoryzowane zmiany mogą być dozwolone, jeśli są gotowe poza Edytuj i Kontynuuj. Jeśli chcesz zachować wyniki takiej nieautoryzowanej edycji, musisz zatrzymać debugowanie i ponownie uruchomić aplikację.

 Polecenie Edytuj i Kontynuuj jest obsługiwane w aplikacjach platformy UWP dla systemu Windows 10 oraz dla aplikacji x86 i x64 przeznaczonych dla komputerów z systemem .NET Framework 4,6 lub nowszym (.NET Framework jest tylko wersja klasyczna).

 > [!NOTE]
 > Nieobsługiwane aplikacje i platformy obejmują ASP.NET 5, Silverlight 5 i Windows 8.1.

 Polecenia Edytuj i Kontynuuj nie są obsługiwane po rozpoczęciu debugowania za pomocą **dołączania do procesu**. Tryb Edytuj i Kontynuuj nie jest obsługiwany w przypadku zoptymalizowanego kodu lub kodu zarządzanego i natywnego. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Tematy w tej sekcji zawierają dodatkowe informacje na temat sposobu korzystania z tej funkcji oraz tego, jakiego rodzaju zmiany są niedozwolone.

## <a name="in-this-section"></a>W tej sekcji
 [Instrukcje: stosowanie edycji w trybie przerwania za pomocą Edytuj i Kontynuuj](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) Wyjaśnia, jak zastosować edycje kodu w trybie przerwania.

 [Obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md) Opisuje rodzaje edycji, które nie mogą być wykonywane w [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] Edytuj i Kontynuuj.

## <a name="related-sections"></a>Sekcje pokrewne
 [Edytuj i Kontynuuj](../debugger/edit-and-continue.md) Zawiera listę tematów dotyczących Edytuj i Kontynuuj.
