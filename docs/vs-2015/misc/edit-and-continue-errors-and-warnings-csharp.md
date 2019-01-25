---
title: Edycja i kontynuowanie przy błędach i ostrzeżeniach (C#) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.csharp.enc.error_4001
- vs.csharp.enc.error_4034
- vs.csharp.enc.error_4003
- vs.csharp.enc.error_4026
- vs.csharp.enc.error_4032
- vs.csharp.enc.error_4017
- vs.csharp.enc.error_4053
- vs.csharp.enc.error_4024
- vs.csharp.enc.error_4012
- vs.csharp.enc.error_4066
- vs.csharp.enc.error_4020
- vs.csharp.enc.error_4008
- vs.csharp.enc.error_4033
- vs.csharp.enc.error_4014
- vs.csharp.enc.error_4023
- vs.csharp.enc.error_4011
- vs.csharp.enc.error_4006
- vs.csharp.enc.error_4059
- vs.csharp.enc.error_4015
- vs.csharp.enc.error_4018
- vs.csharp.enc.error_4028
- vs.csharp.enc.error_4013
- vs.csharp.enc.error_4009
- vs.csharp.enc.error_4021
- vs.csharp.enc.error_4065
- vs.csharp.enc.error_4029
- vs.csharp.enc.error_4058
- vs.csharp.enc.error_4019
- vs.csharp.enc.error_4007
- vs.csharp.enc.error_4052
- vs.csharp.enc.error_4025
- vs.csharp.enc.error_4055
- vs.csharp.enc.error_4022
- vs.csharp.enc.error_4002
- vs.csharp.enc.error_4016
- vs.csharp.enc.error_4043
- vs.csharp.enc.error_4027
- vs.csharp.enc.error_4054
- vs.csharp.enc.error_4004
- vs.csharp.enc.error_4010
- vs.csharp.enc.error_4030
- vs.csharp.enc.error_4005
- vs.csharp.enc.error_4035
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], errors and warnings
- errors [C#], debugging
- errors [debugger], Edit and Continue
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 36d2665eef36e0e233cf02d241f550f3e701800f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805520"
---
# <a name="edit-and-continue-errors-and-warnings-c"></a>Edycja i kontynuowanie przy błędach i ostrzeżeniach (C#)
Dokonano edycji sekcji kodu, który nie jest dozwolona w Visual C# Edytuj i Kontynuuj.  
  
 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] Edytuj i Kontynuuj umożliwia zatrzymują wykonywanie programu w trybie przerwania, wprowadzić zmiany na wykonywanie kodu, a następnie Wznów działanie programu przy użyciu nowo zarejestrowanych zmian.  
  
 Zwykle otrzymują kod deklaratywny zmian w strukturze publiczne klasy, a niektóre zmiany wprowadzane do metody, właściwości treści lub prywatnej deklaracje w obrębie klasy nie są dozwolone. Jeśli to możliwe, Edytuj i Kontynuuj oznacza kod, którego nie można edytować jako szary jasny i wyświetla komunikat o błędzie.  
  
 Aby uzyskać więcej informacji na temat obsługiwanych edycji w Edytuj i Kontynuuj dla [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], zobacz [obsługiwane zmiany kodu (C#)](../debugger/supported-code-changes-csharp.md). Aby uzyskać więcej informacji na temat wystąpienia określonego błędu lub ostrzeżenia, możesz wyszukiwać i Publikuj w sieci MSDN [forum Visual C# IDE](http://go.microsoft.com/fwlink/?LinkId=214693).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Na **debugowania** menu, wybierz **Cofnij** Aby cofnąć zmianę.  
  
     —lub—  
  
2.  Zatrzymaj sesję debugowania, edytować i rozpocznij nową sesję debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)