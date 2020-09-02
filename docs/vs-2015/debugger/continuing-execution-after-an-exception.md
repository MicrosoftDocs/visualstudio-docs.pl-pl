---
title: Kontynuowanie wykonania po wystąpieniu wyjątku | Microsoft Docs
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
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702264"
---
# <a name="continuing-execution-after-an-exception"></a>Kontynuowanie wykonania po wyjątkach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy debuger przerywa wykonywanie z powodu wyjątku, zostanie wyświetlone okno dialogowe. W przypadku Visual Basic lub C# zostanie wyświetlone okno dialogowe [Asystent wyjątków](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) domyślnie. W przypadku języka C++ zostanie wyświetlone okno dialogowe starszy **wyjątek** . Jeśli używasz Visual Basic lub C#, ale **Asystent wyjątków** został wyłączony w oknie dialogowym **Opcje** , zostanie wyświetlone okno dialogowe **wyjątek** .  
  
 Gdy pojawi się okno dialogowe **Asystent wyjątków** lub **wyjątek** , możesz spróbować rozwiązać problem, który spowodował wyjątek.  
  
## <a name="managed-code"></a>Kod zarządzany  
 W kodzie zarządzanym można kontynuować wykonywanie w tym samym wątku po wystąpieniu nieobsłużonego wyjątku. **Asystent wyjątków** cofa stos wywołań do punktu, w którym został zgłoszony wyjątek.  
  
## <a name="native-code"></a>Kod natywny  
 W natywnych C/C++ dostępne są dwie opcje:  
  
- Możesz kliknąć przycisk **Przerwij** i spróbować rozwiązać problem. Gdy jesteś w trybie przerwania, można odtworzyć stos wywołań, klikając prawym przyciskiem myszy ramkę w oknie **stos wywołań** i wybierając pozycję **odwinięcie do tej ramki** w menu skrótów. W przypadku kontynuowania debugowania zostanie wyświetlone okno dialogowe **wyjątek** , jeśli problem nie został rozwiązany. W przeciwnym razie okno dialogowe **wyjątek** nie zostanie wyświetlone ponownie.  
  
- Możesz kliknąć przycisk **Kontynuuj** , aby kontynuować wykonywanie bez próby rozwiązania problemu. Zostanie wyświetlone okno dialogowe **wyjątek** .  
  
## <a name="mixed-code"></a>Kod mieszany  
 Jeśli wystąpił nieobsługiwany wyjątek podczas debugowania kodu natywnego i zarządzanego, ograniczenia systemu operacyjnego uniemożliwiają rozwinięcia stosu wywołań. Jeśli spróbujesz odwinąć stos wywołań za pomocą menu skrótów, komunikat o błędzie wyjaśnia, że debuger nie może wycofać się z nieobsłużonego elementu, z wyjątkiem debugowania kodu mieszanego.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)
