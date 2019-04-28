---
title: 'Instrukcje: Wychodzenie z kodu zarządzanego, gdy ramek natywnych brakuje oknie stosu wywołań | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1672ba8e6bcf66973a5cd32be3fb03821750e3f2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442732"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Instrukcje: Wychodzenie z kodu zarządzanego, gdy ramek natywnych brakuje oknie stosu wywołań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli kod ma ramek natywnych, które są niewidoczne w **stos wywołań** oknie przechodzenie krok po kroku z kodu zarządzanego, mogą dawać nieoczekiwane wyniki. Jako obejście tego problemu, możesz używać punktu przerwania, a nie **Step Out**.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Aby wychodzenie z kodu zarządzanego, gdy wyświetlanie stosu wywołań brakuje ramek natywnych  
  
1. W kodzie natywnym Ustaw punkt przerwania po wywołaniu kodu zarządzanego.  
  
2. Na **debugowania** menu, wybierz **Kontynuuj**.  
  
     Po ukończeniu wywołania zarządzanego, wykonanie zostanie zatrzymane w punkcie przerwania w kodzie natywnym.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)
