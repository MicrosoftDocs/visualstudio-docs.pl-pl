---
title: Opcje, Edytor tekstu, C/C++, widok
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: b15952c8262ea1e8dec1e89816a5887f9bfe9bf6
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461270"
---
# <a name="options-text-editor-cc-view"></a>Opcje, Edytor tekstu, C/C++, widok

Za pomocą tych stron właściwości można zmienić domyślne zachowanie edytora kodu podczas programowania w języku C lub C++.

Aby uzyskać dostęp do tej strony właściwości, wybierz**Opcje** **Narzędzia** > i rozwiń **Edytor tekstu**, a następnie **C/C++** , a następnie wybierz pozycję **Widok**.

## <a name="code-squiggles"></a>Zawijanie kodu

Można włączać lub wyłączać następujące ustawienia, aby zarządzać sposobem, w jaki Edytor tekstu obsługuje zygzaki kodu dla C++C i:

- **Makra w pominiętych regionach przeglądania** — definiuje sposób wyróżniania makr, które znajdują się w pominiętych regionach przez bazę danych przeglądania, takie jak makra, których definicje zawierają nawiasy klamrowe.

- **Makra konwertowane na wyrażenie constexpr** — definiuje sposób wyróżniania definicji makr, które mogą `constexpr` być konwertowane na definicje.

## <a name="inactive-code"></a>Kod nieaktywny

- **Pokaż nieaktywne bloki** — nieaktywne bloki preprocesora są kolorowane w inny sposób.

- **Wyłącz** nieprzezroczystość nieaktywnego kodu — pełny kolor, a nie krycie, jest używany dla nieaktywnych bloków kodu.

- **Procent** nieprzezroczystości nieaktywnego kodu — procent krycia dla nieaktywnych bloków kodu.

## <a name="miscellaneous"></a>Różne

- **Wyliczanie zadań komentarzy** — Skanuj pliki Open Source dla programu vs i zgłoś je w oknie Lista zadań.

- Wyróżnij pasujące tokeny — Wyróżnij otaczające nawiasy lub składnię pasujące do miejsca, w którym znajduje się kursor.

## <a name="outlining"></a>Tworzenie konspektu

- **Włącz tworzenie konspektu — umożliwia** wprowadzanie trybu konspektu podczas otwierania pliku.

- **Zakreśl regiony dyrektywy** pragma `#pragma` — automatycznie konspekty bloków regionów.

- **Konspekt bloków instrukcji** — automatyczne konspekty bloków instrukcji.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoryzacja w C++ (blog VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
