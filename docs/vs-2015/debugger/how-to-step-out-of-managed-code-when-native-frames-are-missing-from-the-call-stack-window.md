---
title: 'Instrukcje: Wyjdź z kodu zarządzanego w przypadku braku ramek natywnych w oknie stosu wywołań | Microsoft Docs'
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
ms.openlocfilehash: 63bd55fd254dd263540a9161e8579ea6600e97f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690098"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Porady: wychodzenia z kodu zarządzanego gdy w oknie stosu wywołań brakuje ramek natywnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli kod zawiera natywne ramki, które są niewidoczne w oknie **stosu wywołań** , przechodzenie z kodu zarządzanego może dać nieoczekiwane wyniki. Jako obejście, można użyć punktu przerwania zamiast **krokowo**.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Aby wycofać kod zarządzany, gdy brakuje ramek natywnych na ekranie stosu wywołań  
  
1. W kodzie natywnym Ustaw punkt przerwania lokalizacji po wywołaniu kodu zarządzanego.  
  
2. W menu **debugowanie** wybierz polecenie **Kontynuuj**.  
  
     Gdy zarządzane wywołanie zostanie zakończone, wykonywanie zostanie zatrzymane w punkcie przerwania w kodzie natywnym.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)
