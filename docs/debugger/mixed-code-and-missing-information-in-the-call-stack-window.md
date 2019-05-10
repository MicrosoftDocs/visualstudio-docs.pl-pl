---
title: Mieszane kodu i brakujące informacje w oknie stosu wywołań | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 025591ffea4d6746f87e5f1240cd226fa291d116
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905512"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Kod mieszany i brakujące informacje w oknie stosu wywołań
Ze względu na różnice stosy wywołań dla kodu zarządzanego i natywnego debuger zawsze nie można wyświetlić pełny stos wywołań, gdy kod wpisuje mieszanego. Gdy kod natywny wywołuje kod zarządzany, możesz zauważyć poniższe niezgodności w **stos wywołań** okna:

- Ramka natywna bezpośrednio nad kod zarządzany może być brak **stos wywołań** okna. Aby uzyskać więcej informacji, zobacz [jak: Wychodzenie z kodu zarządzanego, gdy ramek natywnych brakuje oknie stosu wywołań](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).

- Dla aplikacji w trybie mieszanym uruchomiony poza debugerem **stos wywołań** okno może być wyświetlany tylko kodu zarządzanego i Brak ramek natywnych będą widoczne.

  Oba przypadki są stosunkowo rzadkie. W najbardziej macierzystych wywołań do kodu zarządzanego stosy wywołań są poprawnie wyświetlane.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)