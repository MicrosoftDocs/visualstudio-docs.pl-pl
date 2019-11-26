---
title: Edytuj i Kontynuuj błędy i ostrzeżenia (C#) | Microsoft Docs
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
ms.openlocfilehash: d0865e06c5abb5faccce51a2bc38bb223f7fa3eb
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299284"
---
# <a name="edit-and-continue-errors-and-warnings-c"></a>Edycja i kontynuowanie przy błędach i ostrzeżeniach (C#)
Dokonano edycji w sekcji kodu, która nie jest dozwolona w programie Visual C# Edit i Kontynuuj.  
  
 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] Edytuj i Kontynuuj umożliwia zatrzymanie wykonywania programu w trybie przerwania, wprowadzanie zmian w kodzie wykonywania, a następnie wznowienie wykonywania programu przy użyciu nowo wprowadzonych zmian.  
  
 Deklaratywne zmiany kodu, które mają wpływ na strukturę publiczną klasy, są ogólnie zabronione, a niektóre zmiany, które mogą zostać wprowadzone do metody, treści właściwości lub deklaracji prywatnych w klasie, są niedozwolone. Jeśli to możliwe, Edytuj i Kontynuuj oznacza kod, którego nie można edytować w kolorze szarym i wyświetla komunikat o błędzie.  
  
 Aby uzyskać więcej informacji na temat obsługiwanych edycji w obszarze Edytuj i Kontynuuj dla [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], zobacz [obsługiwaneC#zmiany kodu ()](../debugger/supported-code-changes-csharp.md). Jeśli potrzebujesz więcej informacji na temat konkretnego błędu lub ostrzeżenia, możesz wyszukiwać lub publikować na forum MSDN [Visual C# IDE](https://go.microsoft.com/fwlink/?LinkId=214693).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. W menu **Debuguj** wybierz polecenie **Cofnij** , aby cofnąć zmianę.  
  
     lub  
  
2. Zatrzymaj sesję debugowania, wprowadź zmiany i Rozpocznij nową sesję debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)