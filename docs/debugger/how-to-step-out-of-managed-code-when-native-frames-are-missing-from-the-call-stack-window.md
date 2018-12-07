---
title: Krok poza C# kodem w przypadku stosu wywołań brakuje ramek natywnych | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 741afb6befdbc29cafab39c3c9b0d7bb2761d7b1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057655"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Porady: wychodzenia z kodu zarządzanego gdy w oknie stosu wywołań brakuje ramek natywnych

Jeśli kod ma ramek natywnych, które są niewidoczne w **stos wywołań** oknie przechodzenie krok po kroku z kodu zarządzanego, mogą dawać nieoczekiwane wyniki. Jako obejście tego problemu, możesz używać punktu przerwania, a nie **Step Out**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Wychodzenie z kodu zarządzanego, gdy wyświetlanie stosu wywołań brakuje ramek natywnych

1.  W kodzie natywnym Ustaw punkt przerwania po wywołaniu kodu zarządzanego.

2.  Na **debugowania** menu, wybierz **Kontynuuj**.

     Po ukończeniu wywołania zarządzanego, wykonanie zostanie zatrzymane w punkcie przerwania w kodzie natywnym.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)