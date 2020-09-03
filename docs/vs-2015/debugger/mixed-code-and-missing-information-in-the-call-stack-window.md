---
title: Kod mieszany i brakujące informacje w oknie stosu wywołań | Microsoft Docs
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
manager: jillfra
ms.openlocfilehash: 3995e14379fa4bd3ebd5cc276613c288b4437d35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193280"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Kod mieszany i brakujące informacje w oknie stosu wywołań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ze względu na różnice między stosami wywołań dla kodu zarządzanego i natywnego debuger nie może zawsze pokazać kompletnego stosu wywołań, gdy typy kodu są mieszane. Gdy kod natywny wywołuje kod zarządzany, można zauważyć następujące rozbieżności w oknie **stosu wywołań** :  
  
- W oknie **stosu wywołań** może brakować ramki natywnej bezpośrednio nad kodem zarządzanym. Aby uzyskać więcej informacji, zobacz [jak: Wyjdź z kodu zarządzanego, gdy w oknie stosu wywołań brakuje ramek natywnych](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- W przypadku aplikacji w trybie mieszanym uruchomionych poza debugerem okno **stos wywołań** może wyświetlać tylko kod zarządzany i żadna z ramek natywnych nie będzie widoczna.  
  
  Oba przypadki są dość rzadkie. W większości natywnych wywołań do kodu zarządzanego, stosy wywołań są wyświetlane poprawnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)
