---
title: Określ wersję .NET Framework debugowania | Microsoft Docs
description: Określ starszą wersję .NET Framework debugowania. Debuger Visual Studio obsługuje debugowanie starszych wersji .NET Framework, a także bieżącą wersję.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 83b30067530b9a48769879f3a222fee2afa725c0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384671"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Określanie starszej wersji .NET Framework debugowania (C#, Visual Basic, F#)

Debuger Visual Studio obsługuje debugowanie starszych wersji programu Microsoft .NET Framework, a także bieżącej wersji. Jeśli uruchamiasz aplikację z Visual Studio, debuger zawsze może zidentyfikować poprawną wersję .NET Framework dla debugej aplikacji. Jeśli jednak aplikacja jest już uruchomiona i rozpoczniesz debugowanie przy użyciu polecenia **Dołącz** do , debuger może nie zawsze być w stanie zidentyfikować starszą wersję .NET Framework. W takim przypadku zostanie wyświetlony komunikat o błędzie z komunikatem:

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

W rzadkich przypadkach, w których występuje ten błąd, można ustawić klucz rejestru, aby wskazać debugerowi, której wersji użyć.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Aby określić wersję .NET Framework debugowania

1. W katalogu Windows\Microsoft.NET\Framework znajdź wersje .NET Framework zainstalowane na maszynie. Numery wersji wyglądają podobnie do tych:

    `V1.1.4322`

    Zidentyfikuj prawidłowy numer wersji i zanotuj go.

2. Uruchom Edytor **rejestru** (regedit).

3. W **Edytorze rejestru** otwórz folder HKEY_LOCAL_MACHINE rejestru.

4. Przejdź do: \\ HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Jeśli klucz nie istnieje, kliknij prawym przyciskiem myszy pozycję HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, a następnie kliknij **pozycję Nowy klucz.** Nadaj noweowi kluczowi nazwę `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` .

5. Po przejściu do adresu {449EC4CC-30D2-4032-9256-EE18EB41B62B}poszukaj w **kolumnie Name** i znajdź klucz CLRVersionForDebugging.

   1. Jeśli klucz nie istnieje, kliknij prawym przyciskiem myszy pozycję {449EC4CC-30D2-4032-9256-EE18EB41B62B}, a następnie kliknij pozycję Nowa wartość **ciągu**. Następnie kliknij prawym przyciskiem myszy nową wartość ciągu, kliknij polecenie **Zmień nazwę** i wpisz `CLRVersionForDebugging` .

6. Kliknij dwukrotnie **pozycję CLRVersionForDebugging.**

7. W **polu Edytuj ciąg** wpisz .NET Framework wersji w **polu** Wartość. Na przykład: V1.1.4322

8. Kliknij przycisk **OK**.

9. Zamknij Edytor **rejestru**.

     Jeśli po rozpoczęciu debugowania nadal pojawia się komunikat o błędzie, sprawdź, czy numer wersji został poprawnie wprowadzony w rejestrze. Sprawdź również, czy używasz wersji programu .NET Framework obsługiwanej przez Visual Studio. Debuger jest zgodny z bieżącą .NET Framework i poprzednimi wersjami, ale może nie być zgodny z przyszłymi wersjami.

## <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)