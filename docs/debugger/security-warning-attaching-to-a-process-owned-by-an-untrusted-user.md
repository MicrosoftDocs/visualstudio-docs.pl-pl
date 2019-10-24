---
title: 'Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu | Microsoft Docs'
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
ms.openlocfilehash: 05b78ea0ca06a0ba9670e61cc065cf539ea21ebc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729776"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub nie masz do nich pełnego zaufania, nie dołączaj do tego procesu
To okno dialogowe ostrzeżenia pojawia się po dołączeniu do procesu, który zawiera częściowo zaufany kod lub jest własnością niezaufanego użytkownika bezpośrednio przed dołączeniem. Niezaufany proces, który zawiera złośliwy kod, ma możliwość uszkodzenia komputera wykonującego debugowanie. Jeśli masz przyczynę anulowania zaufania procesu, kliknij przycisk **Anuluj** , aby zapobiec debugowaniu.

 Aby pominąć to ostrzeżenie podczas debugowania wiarygodnego scenariusza, Zamknij program Visual Studio i ustaw wartość tego klucza rejestru na 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, a następnie ponownie uruchom program Visual Studio. Po zakończeniu debugowania scenariusza Zresetuj wartość na 0 i ponownie uruchom program Visual Studio.

 "Zaufani użytkownicy" obejmują siebie, a także zestaw standardowych użytkowników, którzy są zwykle zdefiniowani na komputerach, na których zainstalowano .NET Framework, takich jak `aspnet`, `localsystem`, `networkservice` i `localservice`.

## <a name="uielement-list"></a>Lista elementów UI
 Nazwa nazwy zestawu żądanego do debugowania

 Bieżący użytkownik użytkownika

 Dołącz naciśnięcie klawisza, aby kontynuować debugowanie przez dołączenie

 Nie dołączaj, nie dołączaj do procesu

## <a name="see-also"></a>Zobacz także
- [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)