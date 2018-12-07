---
title: Wyświetlanie kodu dezasemblacji w debugerze | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 10/30/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c35432bdd01b9b79c2afaa266d8078caf04bd62b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063839"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Wyświetlanie kodu dezasemblacji w debugerze programu Visual Studio (C#, C++, Visual Basic F#)

**Dezasemblacji** okno pokazuje kod zestawu odpowiadający instrukcjom utworzonym przez kompilator. Jeśli debugujesz kod zarządzany w instrukcjach zestawu odnoszą się do kodu macierzystego, utworzony przez kompilator Just-in-Time (JIT), a nie języka Microsoft intermediate language (MSIL) utworzony przez kompilator programu Visual Studio.

> [!NOTE]
> W pełni wykorzystać **dezasemblacji** okna, zrozumieć i Naucz się podstaw [programowania języka asembler](https://wikipedia.org/wiki/Assembly_language).

Ta funkcja jest dostępna tylko jeśli włączone jest debugowanie na poziomie adresów. Nie jest dostępna dla skryptu lub debugowania SQL.

Oprócz instrukcje montażu **dezasemblacji** okna można wyświetlić następujące informacje opcjonalne:

- Adres pamięci, w którym znajduje się każdą instrukcję. Dla natywnych aplikacji jest to adres pamięci rzeczywistych. Dla języka Visual Basic lub C#, to przesunięcie od początku funkcji.

- Kod źródłowy, z którego pochodzi kod zestawu.

- Możesz pisać kod w bajtach, oznacza to, reprezentacje bajt rzeczywistą lub instrukcji MSIL.

- Nazwy symboli dla adresów pamięci.

- Numery wierszy odpowiadających do kodu źródłowego.

Instrukcje języka asemblera składają się z *mnemonik*, skróty nazw instrukcji, które są i *symbole* dla zmiennych, rejestrów i stałe. Każdą instrukcję języka maszyny jest reprezentowany przez jeden język asemblera skrót klawiszowy opcjonalnie następuje jeden lub więcej symboli.

Kod zestawu odgrywa rejestry procesora lub dla kodu zarządzanego, rejestruje środowiska uruchomieniowego języka wspólnego. Możesz użyć **dezasemblacji** okna wraz z **rejestruje** okno, które można sprawdzić zawartość rejestru.

Aby wyświetlić instrukcje kodu maszynowego w ich pierwotne forma liczbowa, a nie jako język asemblera, użyj **pamięci** okna lub wybierz **bajty kodu** z menu skrótów na liście **dezasemblacji**  okna.

## <a name="use-the-disassembly-window"></a>Korzystanie z okna dezasemblacji

Aby włączyć **dezasemblacji** okna, w obszarze **narzędzia** > **opcje** (lub **narzędzia**  >  **Opcje**) > **debugowanie**, wybierz opcję **Włącz debugowanie na poziomie adresów**.

Aby otworzyć **dezasemblacji** okna podczas debugowania, wybierz opcję **Windows** > **dezasemblacji** lub naciśnij **Alt** + **8**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

Opcjonalne informacje należy włączyć lub wyłączyć, kliknij prawym przyciskiem myszy **dezasemblacji** oknie i ustawić lub wyczyścić odpowiednie opcje w menu skrótów.

Żółta strzałka na lewym marginesie oznacza bieżący punkt wykonania. Dla kodu natywnego punkt wykonania odpowiada licznik programu procesora CPU. Ta lokalizacja zawiera następnej instrukcji, która zostanie wykonana w programach.

## <a name="see-also"></a>Zobacz także

* [Stronicowanie w górę lub w dół w pamięci](../debugger/how-to-page-up-or-down-in-memory.md)
* [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
* [Porady: Korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)