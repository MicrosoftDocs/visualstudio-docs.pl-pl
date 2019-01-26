---
title: 'Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub niepewne, nie dołączaj do tego procesu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17511c5f89ca40cc002a80da955df10c8773b97c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952187"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub nie masz do nich pełnego zaufania, nie dołączaj do tego procesu
To okno dialogowe ostrzeżenia pojawia się po dołączeniu do procesu, który zawiera kod częściowo zaufany lub właścicielem jest niezaufanego użytkownika natychmiast, zanim wystąpi dołączanie. Niezaufane procesu, który zawiera złośliwy kod ma potencjalnie uszkodzić komputer podczas debugowania. Jeśli masz powód, aby obdarzać procesu, a następnie kliknij przycisk **anulować** zapobiegające debugowania.  
  
 Aby pominąć to ostrzeżenie podczas debugowania uzasadnione scenariusz, zamknij program Visual Studio i ustawić wartość tego klucza rejestru 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, a następnie ponownie uruchom program Visual Studio. Po zakończeniu debugowania w scenariuszu, Zresetuj wartość 0, a następnie uruchom ponownie program Visual Studio.  
  
 "Zaufanych użytkowników" te obejmują samodzielnie oraz zestaw standardowych użytkowników, którzy są zazwyczaj definiowane na komputerach, które zostały zainstalowane, takie jak w programie .NET Framework `aspnet`, `localsystem`, `networkservice`, i `localservice`.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 Nazwa  
 Nazwa zestawu, wymagane do debugowania  
  
 Użytkownik  
 Bieżący użytkownik  
  
 Dołącz  
 Naciśnij klawisz, aby kontynuować debugowanie przez dołączenie  
  
 Nie dołączaj  
 Nie dołączaj do procesu  
  
## <a name="see-also"></a>Zobacz też  
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)