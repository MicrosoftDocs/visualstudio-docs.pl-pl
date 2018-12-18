---
title: 'Porady: Ustawianie nazw wątków w kodzie zarządzanym | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 585c372a5ffcb71fcc8a2f7e56bb95380b3c41ca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729524"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Porady: ustawianie nazw wątków w kodzie zarządzanym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nazwy wątków jest możliwe w dowolnej wersji programu Visual Studio. Nazewnictwo wątku jest przydatne do śledzenia wątków w **wątków** okna. Ponieważ **wątków** okno nie jest dostępna w wersjach programu Visual Studio Express, wątek nazewnictwa ma niewielkie narzędzie w wersji Express.  
  
 Aby Ustawianie nazw wątków w kodzie zarządzanym, użyć <xref:System.Threading.Thread.Name%2A> właściwości.  
  
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
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Instrukcje: ustawianie nazw wątków w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md)



