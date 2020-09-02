---
title: Tworzenie widoków niestandardowych obiektów zarządzanych | Microsoft Docs
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f5247a56667f5715d9f155c662eb333967878d71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "73188650"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Tworzenie niestandardowych widoków zarządzanych obiektów (C#, Visual Basic, F #, C++/CLI)
Możesz dostosować sposób, w jaki program Visual Studio Wyświetla typy danych w zmiennych debugera systemu Windows.

## <a name="attributes"></a>Atrybuty

W językach C#, Visual Basic, F # i C++ (tylko kod C++/CLI) można dodać rozszerzenia dla danych niestandardowych przy użyciu <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , <xref:System.Diagnostics.DebuggerDisplayAttribute> , i <xref:System.Diagnostics.DebuggerBrowsableAttribute> .

W kodzie .NET Framework 2,0 Visual Basic nie obsługuje atrybutu DebuggerBrowsable. To ograniczenie jest usuwane w nowszych wersjach programu .NET.

## <a name="visualizers"></a>Wizualizatory

Można napisać wizualizator do wyświetlania dowolnego zarządzanego typu danych. Aby uzyskać więcej informacji, zobacz [jak: napisać wizualizator](create-custom-visualizers-of-data.md).

> [!NOTE]
> W przypadku kodu C++ można dodać niestandardowe rozszerzenia typu danych za pomocą struktury Natvis, zgodnie z opisem w temacie [Tworzenie niestandardowych widoków obiektów C++ w debugerze](create-custom-views-of-native-objects.md).

## <a name="see-also"></a>Zobacz też

- [Określ debuger, który ma być wyświetlany przy użyciu atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Poinformuj debugera o typie, który ma być wyświetlany przy użyciu atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Okna wyrażeń kontrolnych i szybkich wyrażeń kontrolnych](../debugger/watch-and-quickwatch-windows.md)
- [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
