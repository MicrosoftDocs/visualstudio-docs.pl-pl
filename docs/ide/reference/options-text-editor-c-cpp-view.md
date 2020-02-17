---
title: Opcje, Edytor tekstu, C/C++, widok
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 95963245b15828f374e9812a9bb09d015b21a94b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278692"
---
# <a name="options-text-editor-cc-view"></a>Opcje, Edytor tekstu, C/C++, widok

Za pomocą tych stron właściwości można zmienić domyślne zachowanie edytora kodu podczas programowania w języku C lub C++.

Aby uzyskać dostęp do tej strony właściwości, wybierz **Narzędzia** > **Opcje** i rozwiń **Edytor tekstu**, a następnie **C/C++** , a następnie wybierz pozycję **Widok**.

## <a name="code-squiggles"></a>Zawijanie kodu

Można włączać lub wyłączać następujące ustawienia, aby zarządzać sposobem, w jaki Edytor tekstu obsługuje zygzaki kodu dla C++C i:

- **Makra w pominiętych regionach przeglądania** — definiuje sposób wyróżniania makr, które znajdują się w pominiętych regionach przez bazę danych przeglądania, takie jak makra, których definicje zawierają nawiasy klamrowe.

- **Makra konwertowane na wyrażenie constexpr** — definiuje sposób wyróżniania definicji makr, które mogą być konwertowane na definicje `constexpr`.

## <a name="inactive-code"></a>Kod nieaktywny

- **Pokaż nieaktywne bloki** — nieaktywne bloki preprocesora są kolorowane w inny sposób.

- Wyłącz nieprzezroczystość **nieaktywnego kodu** — pełny kolor, a nie krycie, jest używany dla nieaktywnych bloków kodu.

- **Procent nieprzezroczystości nieaktywnego kodu** — procent krycia dla nieaktywnych bloków kodu.

## <a name="miscellaneous"></a>Różne

- **Wyliczanie zadań komentarzy** — Skanuj pliki Open Source dla programu vs i zgłoś je w oknie Lista zadań.

- **Wyróżnij pasujące tokeny** — Wyróżnij otaczające nawiasy lub składnię pasujące do miejsca, w którym znajduje się kursor.

## <a name="outlining"></a>Tworzenie konspektu

- **Włącz tworzenie konspektu — umożliwia** wprowadzanie trybu konspektu podczas otwierania pliku.

- **Zakreśl regiony dyrektywy pragma** — automatycznie Wykreśl bloki regionu `#pragma`.

- **Konspekt bloków instrukcji** — automatyczne konspekty bloków instrukcji.

## <a name="see-also"></a>Zobacz też

- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoryzacja w C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
