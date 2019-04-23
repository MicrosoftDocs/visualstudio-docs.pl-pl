---
title: Kontynuowanie wykonania po wystąpieniu wyjątku | Dokumentacja firmy Microsoft
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
- VB
- CSharp
- C++
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a43983846263fa49a7ff501b0d87c460990e8a37
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105477"
---
# <a name="continuing-execution-after-an-exception"></a>Kontynuowanie wykonania po wyjątkach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kiedy debuger przerywa wykonywanie z powodu wyjątku, pojawi się okno dialogowe. Dla języka Visual Basic lub C#, zostanie wyświetlony [Asystenta wyjątków](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) okno dialogowe, domyślnie. Dla języka C++, zostanie wyświetlony starszej wersji **wyjątek** okno dialogowe. Jeśli używasz języka Visual Basic lub C#, ale zostały wyłączone **Asystenta wyjątków** w **opcje** zobaczysz okno dialogowe **wyjątek** okno dialogowe.  
  
 Gdy **Asystenta wyjątków** lub **wyjątek** pojawi się okno dialogowe, możesz spróbować rozwiązać ten problem, który spowodował wyjątek.  
  
## <a name="managed-code"></a>Kod zarządzany  
 W kodzie zarządzanym może kontynuować działanie w tym samym wątku, po wystąpieniu nieobsługiwanego wyjątku. **Asystenta wyjątków** rozwija stos wywołań do punktu, w którym został zgłoszony wyjątek.  
  
## <a name="native-code"></a>Kod natywny  
 W natywnym kodzie języka C/C++ masz dwie opcje:  
  
- Możesz kliknąć pozycję **Przerwij** i spróbować naprawić problem. Gdy jesteś w trybie przerwania możesz Odwiń stos wywołań, klikając prawym przyciskiem myszy ramkę w **stos wywołań** okna i wybierając polecenie **Unwind do tej ramki** w menu skrótów. Jeśli będziesz kontynuować debugować, **wyjątek** okno dialogowe pojawi się ponownie, jeśli problem nie został rozwiązany. W przeciwnym razie **wyjątek** nie pojawi się okno dialogowe.  
  
- Możesz kliknąć pozycję **Kontynuuj** do kontynuowania wykonywania bez próby rozwiązać ten problem. **Wyjątek** pojawi się okno dialogowe.  
  
## <a name="mixed-code"></a>Kod mieszany  
 Jeśli napotkasz nieobsługiwany wyjątek podczas debugowania mieszane kodu natywnego i zarządzanego, ograniczenia systemu operacyjnego uniemożliwiają odwijanie stosu wywołań. Jeśli spróbujesz przewijanie stosu wywołań, za pomocą menu skrótów, komunikat o błędzie wyjaśniono, że debuger nie może wykonać odwinięcia z nieobsługiwanego z wyjątkiem podczas debugowania kodu mieszanego.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)
