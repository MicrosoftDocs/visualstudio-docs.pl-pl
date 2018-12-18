---
title: Mieszane kodu i brakujące informacje w oknie stosu wywołań | Dokumentacja firmy Microsoft
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
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f4ae8e527e5f6ce04680c444baad58802bfad48
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788948"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Kod mieszany i brakujące informacje w oknie stosu wywołań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ze względu na różnice stosy wywołań dla kodu zarządzanego i natywnego debuger zawsze nie można wyświetlić pełny stos wywołań, gdy kod wpisuje mieszanego. Gdy kod natywny wywołuje kod zarządzany, możesz zauważyć poniższe niezgodności w **stos wywołań** okna:  
  
- Ramka natywna bezpośrednio nad kod zarządzany może być brak **stos wywołań** okna. Aby uzyskać więcej informacji, zobacz [porady: wychodzenia z kodu zarządzanego, gdy ramek natywnych brakuje oknie stosu wywołań](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- Dla aplikacji w trybie mieszanym uruchomiony poza debugerem **stos wywołań** okno może być wyświetlany tylko kodu zarządzanego i Brak ramek natywnych będą widoczne.  
  
  Oba przypadki są stosunkowo rzadkie. W najbardziej macierzystych wywołań do kodu zarządzanego stosy wywołań są poprawnie wyświetlane.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)





