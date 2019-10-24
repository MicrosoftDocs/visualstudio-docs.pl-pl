---
title: Kod mieszany i brakujące informacje w oknie stosu wywołań | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a314634766618340e3fb69052bc896cae700d4b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731140"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Kod mieszany i brakujące informacje w oknie stosu wywołań
Ze względu na różnice między stosami wywołań dla kodu zarządzanego i natywnego debuger nie może zawsze pokazać kompletnego stosu wywołań, gdy typy kodu są mieszane. Gdy kod natywny wywołuje kod zarządzany, można zauważyć następujące rozbieżności w oknie **stosu wywołań** :

- W oknie **stosu wywołań** może brakować ramki natywnej bezpośrednio nad kodem zarządzanym. Aby uzyskać więcej informacji, zobacz [jak: Wyjdź z kodu zarządzanego, gdy w oknie stosu wywołań brakuje ramek natywnych](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).

- W przypadku aplikacji w trybie mieszanym uruchomionych poza debugerem okno **stos wywołań** może wyświetlać tylko kod zarządzany i żadna z ramek natywnych nie będzie widoczna.

  Oba przypadki są dość rzadkie. W większości natywnych wywołań do kodu zarządzanego, stosy wywołań są wyświetlane poprawnie.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)