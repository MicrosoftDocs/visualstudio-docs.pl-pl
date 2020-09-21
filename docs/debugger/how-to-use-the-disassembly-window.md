---
title: Wyświetlanie kodu demontażu w debugerze | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23f297aa3fc549714a9b6327232a8a0b69c6138f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808171"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Wyświetlanie kodu demontażu w debugerze programu Visual Studio (C#, C++, Visual Basic, F #)

Okno **demontażu** zawiera kod zestawu odpowiadający instrukcjom utworzonym przez kompilator. Jeśli debugujesz kod zarządzany, te instrukcje zestawu odpowiadają kodowi natywnym utworzonym przez kompilator just-in-Time (JIT), a nie języka pośredniego firmy Microsoft (MSIL) utworzonego przez kompilator programu Visual Studio.

> [!NOTE]
> Aby w pełni wykorzystać możliwości okna **demontażu** , poznanie lub poznanie podstaw [programowania w języku asemblera](https://wikipedia.org/wiki/Assembly_language).

Ta funkcja jest dostępna tylko wtedy, gdy włączone jest debugowanie na poziomie adresu. Nie jest on dostępny dla debugowania skryptów i SQL.

Oprócz instrukcji zestawu, w oknie **demontażu** można wyświetlić następujące informacje opcjonalne:

- Adres pamięci, w którym znajduje się każda instrukcja. W przypadku aplikacji natywnych jest to rzeczywisty adres pamięci. W przypadku Visual Basic lub C# jest to przesunięcie od początku funkcji.

- Kod źródłowy, z którego pochodzi kod zestawu.

- Bajty kodu, czyli reprezentacje bajtów rzeczywistej maszyny lub instrukcji MSIL.

- Nazwy symboli dla adresów pamięci.

- Numery wierszy odpowiadające kodowi źródłowej.

Instrukcje dotyczące języka asemblerowego składają się z *symboli*, które są skrótami nazw instrukcji i *symboli* zmiennych, rejestrów i stałych. Każda instrukcja języka maszynowego jest reprezentowana przez jeden znak w języku asemblera, a następnie jeden lub więcej symboli.

Kod zestawu jest w dużym stopniu oparty na rejestrach procesora lub, dla kodu zarządzanego, rejestrów środowiska uruchomieniowego języka wspólnego. Można użyć okna **demontażu** wraz z oknem **rejestry** , co pozwala na badanie zawartości rejestru.

Aby wyświetlić instrukcje dotyczące kodu maszynowego w pierwotnej formie liczbowej, a nie jako język zestawu, użyj okna **pamięć** lub wybierz pozycję **bajty kodu** z menu skrótów w oknie **demontażu** .

## <a name="use-the-disassembly-window"></a>Korzystanie z okna demontażu

Aby włączyć okno **demontaż** , w obszarze **Narzędzia**  >  **Opcje**  >  **debugowania**wybierz pozycję **Włącz debugowanie na poziomie adresu**.

Aby otworzyć okno **demontaż** podczas debugowania, wybierz pozycję **Windows**  >  **demontaż** systemu Windows lub naciśnij klawisz **Alt** + **8**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Aby włączyć lub wyłączyć informacje opcjonalne, kliknij prawym przyciskiem myszy w oknie **demontażu** i ustaw lub wyczyść odpowiednie opcje w menu skrótów.

Żółta strzałka w lewym marginesie oznacza bieżący punkt wykonania. W przypadku kodu natywnego punkt wykonywania odpowiada licznikowi programu procesora CPU. Ta lokalizacja pokazuje następną instrukcję, która zostanie wykonana w programie.

## <a name="see-also"></a>Zobacz też

* [Stronicowanie w górę lub w dół w pamięci](../debugger/how-to-page-up-or-down-in-memory.md)
* [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
* [Instrukcje: korzystanie z okna Rejestry](../debugger/how-to-use-the-registers-window.md)