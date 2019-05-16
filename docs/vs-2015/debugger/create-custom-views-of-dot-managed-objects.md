---
title: Tworzenie niestandardowych widoków obiektów zarządzanych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb5b56404c7ddc99b7999b47cf3c2a899f915efd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702420"
---
# <a name="create-custom-views-of-managed-objects"></a>Tworzenie niestandardowych widoków obiektów zarządzanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można dostosować sposób, w programie Visual Studio Wyświetla typy danych w oknach zmiennych debugera.  
  
## <a name="attributes"></a>Atrybuty  
 W języku C# i Visual Basic, można dodać rozszerzeń dla niestandardowych danych za pomocą <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, i <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 W [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] kodu języka Visual Basic nie obsługuje atrybutu DebuggerBrowsable. To ograniczenie zostało usunięte w nowszych wersjach programu .NET Framework.  
  
## <a name="visualizers"></a>Wizualizatory  
 Można napisać visualizer, aby wyświetlić dowolny typ danych zarządzanych. Aby uzyskać więcej informacji, zobacz [jak: Pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Kod natywny  
 Dla kodu natywnego można dodać rozszerzenia typu danych niestandardowych do autoexp.dat — plik, który znajduje się w katalogu 11.0\Common7\Packages\Debugger Program Files\Microsoft Visual Studio. Instrukcje dotyczące sposobu pisania `autoexp` zasady znajdują się w samym pliku.  
  
> [!CAUTION]
> Struktura tego pliku i składnię autoexp reguł mogą ulec zmianie z jednej wersji programu Visual Studio do następnego.  
  
 Typ natywny widoków można dostosować w taki sposób, przez napisanie expression evaluator dodatku. Aby uzyskać więcej informacji, zobacz [EEAddIn próbki: Debugowanie Expression Evaluator dodatek](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Wyrażenie kontrolne i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
