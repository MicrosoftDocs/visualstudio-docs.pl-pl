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
ms.openlocfilehash: 57480eff4e2ad6e6c33008be6f1bbc2a2f332432
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015098"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Tworzenie niestandardowych widoków obiektów (C#, Visual Basic, C++)
Można dostosować sposób, w programie Visual Studio Wyświetla typy danych w oknach zmiennych debugera.  

## <a name="native-code"></a>Kod natywny

Dla kodu C++, można dodać rozszerzenia typu danych niestandardowych przy użyciu struktury Natvis, zgodnie z opisem w [Tworzenie niestandardowych widoków obiektów natywnych w debugerze](/visualstudio/debugger/create-custom-views-of-native-objects). C + +/ kodu interfejsu wiersza polecenia, możesz również użyć atrybutów opisanych w tym miejscu, w tym artykule.

## <a name="attributes"></a>Atrybuty

W C#, Visual Basic i C++ (C + +/ tylko kodu interfejsu wiersza polecenia), można dodawać rozszerzeń dla niestandardowych danych za pomocą <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, i <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
W [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] kodu języka Visual Basic nie obsługuje atrybutu DebuggerBrowsable. To ograniczenie zostało usunięte w nowszych wersjach programu .NET Framework.    

## <a name="visualizers"></a>Wizualizatory

Można napisać visualizer, aby wyświetlić dowolny typ danych zarządzanych. Aby uzyskać więcej informacji, zobacz [jak: Pisanie wizualizatora](/visualstudio/debugger/create-custom-visualizers-of-data).
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Wyrażenie kontrolne i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)