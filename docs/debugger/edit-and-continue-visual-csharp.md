---
title: Edytuj i Kontynuuj (Visual C#) | Microsoft Docs
description: Edytuj i Kontynuuj jest dostępny dla projektów Visual C#. Dowiedz się, jakie zmiany są obsługiwane i jak można kontrolować, czy są stosowane zmiany.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 375e1db598f925a193def159203ccb7e5c5fdf05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871861"
---
# <a name="edit-and-continue-visual-c"></a>Edytuj i kontynuuj (Visual C#)
 Za pomocą Edytuj i Kontynuuj dla języka C# można wprowadzać zmiany w kodzie w trybie przerwania podczas debugowania. Zmiany można zastosować bez konieczności zatrzymywania i ponownego uruchamiania sesji debugowania. W trybie uruchamiania Edytor źródła jest tylko do odczytu.

 Polecenie Edytuj i Kontynuuj obsługuje większość zmian, które mogą zostać wprowadzone podczas sesji debugowania, ale istnieją pewne wyjątki. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Polecenie Edytuj i Kontynuuj jest obsługiwane w programie platformy UWP w systemie Windows 10 oraz w aplikacjach x86 i x64, które są przeznaczone dla komputerów z systemem .NET Framework 4,6 lub nowszym (.NET Framework jest tylko wersja klasyczna).

 > [!NOTE]
 > Nieobsługiwane aplikacje i platformy obejmują program Silverlight 5 i Windows 8.1.

 Gdy funkcja Edytuj i Kontynuuj jest włączona, obsługiwane zmiany są stosowane automatycznie podczas korzystania z polecenia debugger Execution, takiego jak **Kontynuuj**, **Step**, **Set Next** lub przeprowadź ocenę funkcji w oknie debugera.

 Aby uzyskać więcej informacji, zobacz [How to: use Edit and Continue (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: używanie funkcji Edytuj i kontynuuj (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Pisanie i debugowanie uruchomionego kodu XAML przy użyciu gorącego ponownego ładowania XAML w programie Visual Studio](../xaml-tools/xaml-hot-reload.md)
