---
title: Tworzenie niestandardowych widoków obiektów | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 911f0423184f22919be016691b9333b2f62d1b61
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744801"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Tworzenie niestandardowych widoków obiektów (C#, Visual Basic, C++)
Można dostosować sposób, w programie Visual Studio Wyświetla typy danych w oknach zmiennych debugera.

## <a name="native-code"></a>Kod natywny

Aby uzyskać C++ kodu, możesz dodać dane niestandardowe rozszerzenia typu, przy użyciu struktury Natvis zgodnie z opisem w [Tworzenie niestandardowych widoków C++ obiektów w debugerze](/visualstudio/debugger/create-custom-views-of-native-objects). Aby uzyskać C++/kodu interfejsu wiersza polecenia, możesz również użyć atrybutów opisanych w tym miejscu, w tym artykule.

## <a name="attributes"></a>Atrybuty

W C#, Visual Basic i C++ (C++tylko kod w sposób niezamierzony), można dodawać rozszerzeń dla niestandardowych danych za pomocą <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, i <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

W kodzie .NET Framework 2.0 Visual Basic nie obsługuje atrybutu DebuggerBrowsable. To ograniczenie zostało usunięte w nowszych wersjach programu .NET Framework.

## <a name="visualizers"></a>Wizualizatory

Można napisać visualizer, aby wyświetlić dowolny typ danych zarządzanych. Aby uzyskać więcej informacji, zobacz [jak: Pisanie wizualizatora](/visualstudio/debugger/create-custom-visualizers-of-data).

## <a name="see-also"></a>Zobacz też

- [Polecić debugerowi, co pokazano przy użyciu atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Polecić debugerowi, jakiego typu do wyświetlenia, korzystanie z atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Okna wyrażeń kontrolnych i szybkich wyrażeń kontrolnych](../debugger/watch-and-quickwatch-windows.md)
- [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)