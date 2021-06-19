---
title: Wyświetlanie kodu dekompebracyjnie w | Microsoft Docs
description: Użyj okna Dekompełowanie w Visual Studio, aby wyświetlić kod zestawu odpowiadający instrukcji utworzonych przez kompilator.
ms.custom: SEO-VS-2020
ms.date: 10/30/2018
ms.topic: how-to
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8cc67b2f8136ea426eb56c25fb3c345198701f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387466"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Wyświetlanie kodu dekompełowania w Visual Studio (C#, C++, Visual Basic, F#)

W **oknie** Dekompełtowanie jest wyświetlany kod zestawu odpowiadający instrukcji utworzonych przez kompilator. W przypadku debugowania kodu zarządzanego te instrukcje dotyczące zestawu odpowiadają kodowi natywnemu utworzonemu przez kompilator JIT (Just-in-Time), a nie językowi microsoft intermediate language (MSIL) utworzonemu przez kompilator Visual Studio.

> [!NOTE]
> Aby w pełni korzystać z okna **dekompetatywu,** poznaj lub poznaj podstawy programowania [w języku zestawu.](https://wikipedia.org/wiki/Assembly_language)

Ta funkcja jest dostępna tylko wtedy, gdy debugowanie na poziomie adresu jest włączone. Nie jest ona dostępna dla skryptu ani debugowania SQL.

Poza instrukcjami dotyczącymi zestawu w oknie **Dekompletowanie** mogą być wyświetlane następujące informacje opcjonalne:

- Adres pamięci, na którym znajduje się każda instrukcja. W przypadku aplikacji natywnych jest to rzeczywisty adres pamięci. W Visual Basic lub C# jest to przesunięcie od początku funkcji.

- Kod źródłowy, z którego pochodzi kod zestawu.

- Bajty kodu, czyli reprezentacje bajtów rzeczywistej maszyny lub instrukcji MSIL.

- Nazwy symboli adresów pamięci.

- Numery wiersza odpowiadające kodowi źródłowego.

Instrukcje języka zestawu składają się z *mnemonik*,  które są skrótami nazw instrukcji oraz symboli zmiennych, rejestrów i stałych. Każda instrukcja języka maszynowego jest reprezentowana przez jeden mnemoniczny język zestawu opcjonalnie po którym następuje co najmniej jeden symbol.

Kod zestawu w dużym stopniu zależy od rejestrów procesora lub, w przypadku kodu zarządzanego, rejestrów środowiska uruchomieniowego języka wspólnego. Możesz użyć okna **Dekompełowanie** wraz z oknem **Rejestry,** które umożliwia badanie zawartości rejestru.

Aby wyświetlić instrukcje dotyczące kodu maszynowego w nieprzetworzonej postaci  liczbowej, a nie jako język zestawu, użyj okna Pamięć lub wybierz pozycję Bajty kodu z menu skrótów w oknie  **Dekompasywu.**

## <a name="use-the-disassembly-window"></a>Korzystanie z okna Dekompełtowanie

Aby włączyć okno **Dekompresja,** w **obszarze Narzędzia**  >  **Opcje**  >  **debugowania** wybierz pozycję **Włącz debugowanie na poziomie adresu.**

Aby otworzyć okno **Dekompełtowanie** podczas debugowania, wybierz pozycję Dekompełowanie **systemu Windows** lub naciśnij  >   klawisze **Alt** + **8**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz pozycję **Importuj i Eksportuj ustawienia** **w** menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Aby włączyć lub wyłączyć opcjonalne informacje,  kliknij prawym przyciskiem myszy w oknie Dekompletowanie i ustaw lub wyczyść żądane opcje w menu skrótów.

Żółta strzałka na lewym marginesie oznacza bieżący punkt wykonania. W przypadku kodu natywnego punkt wykonywania odpowiada licznikowi programu procesora CPU. Ta lokalizacja pokazuje następną instrukcję, która zostanie wykonana w programie.

## <a name="see-also"></a>Zobacz też

* [Stronicowanie w górę lub w dół w pamięci](../debugger/how-to-page-up-or-down-in-memory.md)
* [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
* [How to: Use the Registers window (2. 3. 3. 3. 3.](../debugger/how-to-use-the-registers-window.md)