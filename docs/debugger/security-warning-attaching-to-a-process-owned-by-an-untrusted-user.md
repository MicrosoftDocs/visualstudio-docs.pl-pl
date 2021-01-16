---
title: 'Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu | Microsoft Docs'
ms.date: 1/15/2021
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
ms.openlocfilehash: 44f7df253951d90a29c459bf28e6ff1c2279ee54
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533371"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub nie masz do nich pełnego zaufania, nie dołączaj do tego procesu

To okno dialogowe ostrzeżenia pojawia się po dołączeniu do procesu, który zawiera częściowo zaufany kod lub jest własnością niezaufanego użytkownika bezpośrednio przed dołączeniem. Niezaufany proces, który zawiera złośliwy kod, ma możliwość uszkodzenia komputera wykonującego debugowanie. Jeśli masz przyczynę anulowania zaufania procesu, kliknij przycisk **Anuluj** , aby zapobiec debugowaniu.

W scenariuszach IIS można zobaczyć to ostrzeżenie, jeśli używasz niestandardowej puli aplikacji, która nie jest zaufana.

Aby pominąć to ostrzeżenie podczas debugowania wiarygodnego scenariusza:

1. Zamknij program Visual Studio.

1. Ustaw wartość `DisableAttachSecurityWarning` klucza rejestru na 1.

   Znajdź lub Utwórz klucz w obszarze `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger` i ustaw go na 1.

   W programie Visual Studio 2017, jeśli chcesz wyświetlić pełne ustawienia rejestru, musisz załadować gałąź rejestru prywatnego. Aby uzyskać więcej informacji, zobacz [Jak sprawdzić rejestr programu Visual Studio 2017](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md). Przed uruchomieniem programu Visual Studio upewnij się, że gałąź rejestru prywatnego została zwolniona.

1. Uruchom ponownie program Visual Studio.

1. Po zakończeniu debugowania scenariusza Zresetuj wartość na 0 i ponownie uruchom program Visual Studio.

"Zaufani użytkownicy" obejmują siebie, a także zestaw standardowych użytkowników, którzy są zwykle zdefiniowani na komputerach, na których zainstalowano .NET Framework, takich jak `aspnet` ,, `localsystem` `networkservice` i `localservice` .

## <a name="uielement-list"></a>Lista elementów UI

 Nazwa nazwy zestawu żądanego do debugowania

 Bieżący użytkownik użytkownika

 Dołącz naciśnięcie klawisza, aby kontynuować debugowanie przez dołączenie

 Nie dołączaj, nie dołączaj do procesu

## <a name="see-also"></a>Zobacz także
- [Dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
