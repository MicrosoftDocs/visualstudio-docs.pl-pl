---
title: Opcje, Edytor tekstu, C/C++, Widok
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278692"
---
# <a name="options-text-editor-cc-view"></a>Opcje, Edytor tekstu, C/C++, Widok

Użyj tych stron właściwości, aby zmienić domyślne zachowanie edytora kodu podczas programowania w języku C lub C++.

Aby uzyskać dostęp do tej strony właściwości, wybierz pozycję**Opcje** **narzędzi** > i rozwiń pozycję **Edytor tekstu**, następnie **C/C++,** a następnie wybierz polecenie **Wyświetl**.

## <a name="code-squiggles"></a>Squiggles kodu

Można włączyć lub wyłączyć następujące ustawienia, aby zarządzać sposobem, w jaki edytor tekstu obsługuje squiggles kodu dla C i C++:

- **Makra w pominiętych regionach przeglądania** — określa sposób wyróżniania makr, które znajdują się wewnątrz pominiętych regionów przez przeglądającą bazę danych, takich jak makra, których definicje zawierają nawiasy klamrowe.

- **Makra convertible na constexpr** — definiuje sposób wyróżniania definicji `constexpr` makr, które można przekonwertować na definicje.

## <a name="inactive-code"></a>Kod nieaktywny

- **Pokaż nieaktywne bloki** — bloki nieaktywne preprocesora są inaczej barwione.

- **Wyłącz nieaktywne krycie kodu** — jednolity kolor zamiast krycia jest używany dla nieaktywnych bloków kodu.

- **Nieaktywny procent krycia kodu** — procent krycia dla nieaktywnych bloków kodu.

## <a name="miscellaneous"></a>Różne

- **Wyliczaj zadania komentarzy** — skanuj pliki open source w poszukiwaniu tokenów VS i zgłoś je w oknie Lista zadań.

- **Wyróżnij pasujące tokeny** — wyróżnij nawiasy klamrowe lub składnię, która pasuje do miejsca, w którym znajduje się kursor.

## <a name="outlining"></a>Tworzenie konspektu

- **Włącz tworzenie pospektów** — wprowadź tryb tworzenia po otwarciu pliku.

- **Konspekt Regiony Pragmy** — automatycznie konspekt `#pragma` bloków regionów.

- **Bloki instrukcji konspektu** — automatycznie konspekt bloków instrukcji.

## <a name="see-also"></a>Zobacz też

- [Ustawianie opcji Edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoryzowanie w języku C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
