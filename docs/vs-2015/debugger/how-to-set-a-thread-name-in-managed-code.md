---
title: 'Instrukcje: Ustawianie nazwy wątku w kodzie zarządzanym | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b800fbd2f39d75f110a059c70b87a203eb72e7d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157674"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Porady: ustawianie nazw wątków w kodzie zarządzanym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nazewnictwo wątków jest możliwe w dowolnej wersji programu Visual Studio. Nazewnictwo wątków jest przydatne do śledzenia wątków w oknie **wątków** . Ponieważ okno **wątki** nie jest dostępne w wersjach Visual Studio Express, nazwa wątku ma niewielkie narzędzie w wersjach Express.  
  
 Aby ustawić nazwę wątku w kodzie zarządzanym, użyj <xref:System.Threading.Thread.Name%2A> właściwości.  
  
## <a name="example"></a>Przykład  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Porady: ustawianie nazw wątków w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md)
