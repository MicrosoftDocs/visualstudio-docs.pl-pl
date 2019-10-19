---
title: Tworzenie widoków niestandardowych obiektów zarządzanych | Microsoft Docs
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
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578056"
---
# <a name="create-custom-views-of-managed-objects"></a>Tworzenie niestandardowych widoków obiektów zarządzanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz dostosować sposób, w jaki program Visual Studio Wyświetla typy danych w zmiennych debugera systemu Windows.  
  
## <a name="attributes"></a>Atrybuty  
 W C# i Visual Basic można dodawać rozszerzenia dla danych niestandardowych przy użyciu <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> i <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 W [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] kodzie Visual Basic nie obsługuje atrybutu DebuggerBrowsable. To ograniczenie jest usuwane w nowszych wersjach .NET Framework.  
  
## <a name="visualizers"></a>Wizualizatory  
 Można napisać wizualizator do wyświetlania dowolnego zarządzanego typu danych. Aby uzyskać więcej informacji, zobacz [jak: napisać wizualizator](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Kod natywny  
 W przypadku kodu natywnego można dodać niestandardowe rozszerzenia typu danych do pliku autoexp. dat, który znajduje się w programie Files\Microsoft Visual Studio 11.0 \ Common7\Packages\Debugger Directory. Instrukcje dotyczące sposobu pisania reguł `autoexp` znajdują się w samym pliku.  
  
> [!CAUTION]
> Struktura tego pliku i składnia reguł autoexp mogą ulec zmianie z jednej wersji programu Visual Studio na następną.  
  
 Widoki typu natywnego można także dostosować, pisząc dodatek Expression ewaluatora. Aby uzyskać więcej informacji, zobacz [EEAddIn Sample: Debug Expression ewaluatora Add-in](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie   atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)  
 [Używanie atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)    
 [Obejrzyj i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)    
 [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
