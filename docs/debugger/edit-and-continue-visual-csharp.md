---
title: Edytuj i Kontynuuj (wizualizacja C#) | Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5d54673ee46c594bd1a4bea2990d3b9bbe90ce1f
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188188"
---
# <a name="edit-and-continue-visual-c"></a>Edytuj i kontynuuj (Visual C#)
 Za pomocą Edytuj i Kontynuuj C#dla można wprowadzać zmiany w kodzie w trybie przerwania podczas debugowania. Zmiany można zastosować bez konieczności zatrzymywania i ponownego uruchamiania sesji debugowania. W trybie uruchamiania Edytor źródła jest tylko do odczytu.

 Polecenie Edytuj i Kontynuuj obsługuje większość zmian, które mogą zostać wprowadzone podczas sesji debugowania, ale istnieją pewne wyjątki. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany koduC# (i Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Polecenie Edytuj i Kontynuuj jest obsługiwane w programie platformy UWP w systemie Windows 10 oraz w aplikacjach x86 i x64, które są przeznaczone dla komputerów z systemem .NET Framework 4,6 lub nowszym (.NET Framework jest tylko wersja klasyczna).

 > [!NOTE]
 > Nieobsługiwane aplikacje i platformy obejmują ASP.NET 5, Silverlight 5 i Windows 8.1.

 Gdy funkcja Edytuj i Kontynuuj jest włączona, obsługiwane zmiany są stosowane automatycznie podczas korzystania z polecenia debugger Execution, takiego jak **Kontynuuj**, **Step**, **Set Next**lub przeprowadź ocenę funkcji w oknie debugera.

 Aby uzyskać więcej informacji, zobacz [How to: use Edit and ContinueC#()](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: używanie funkcji Edytuj i kontynuuj (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Pisanie i debugowanie uruchomionego kodu XAML przy użyciu gorącego ponownego ładowania XAML w programie Visual Studio](../xaml-tools/xaml-hot-reload.md)
