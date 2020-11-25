---
title: Opcje, Edytor tekstu, C/C++, widok
description: Dowiedz się, jak za pomocą strony widok w sekcji C/C++ zmienić domyślne zachowanie podkreślenia kodu, nieaktywnego kodu, konspektu i innych elementów w programie Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 68d08953ca3c493f3b3e42dd4ddd84bc19bdfd6e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041077"
---
# <a name="options-text-editor-cc-view"></a>Opcje, Edytor tekstu, C/C++, widok

Użyj tych stron właściwości, aby zmienić domyślne zachowanie edytora kodu podczas programowania w C lub C++.

Aby uzyskać dostęp do tej strony właściwości **Tools**, wybierz  >  **Opcje** narzędzia i rozwiń **Edytor tekstu**, a następnie **C/C++**, a następnie wybierz pozycję **Widok**.

## <a name="code-squiggles"></a>Zawijanie kodu

Można włączać lub wyłączać następujące ustawienia, aby zarządzać sposobem, w jaki Edytor tekstu obsługuje zygzaki kodu dla języków C i C++:

- **Makra w pominiętych regionach przeglądania** — definiuje sposób wyróżniania makr, które znajdują się w pominiętych regionach przez bazę danych przeglądania, takie jak makra, których definicje zawierają nawiasy klamrowe.

- **Makra konwertowane na wyrażenie constexpr** — definiuje sposób wyróżniania definicji makr, które mogą być konwertowane na `constexpr` definicje.

## <a name="inactive-code"></a>Kod nieaktywny

- **Pokaż nieaktywne bloki** — nieaktywne bloki preprocesora są kolorowane w inny sposób.

- Wyłącz nieprzezroczystość **nieaktywnego kodu** — pełny kolor, a nie krycie, jest używany dla nieaktywnych bloków kodu.

- **Procent nieprzezroczystości nieaktywnego kodu** — procent krycia dla nieaktywnych bloków kodu.

## <a name="miscellaneous"></a>Różne

- **Wyliczanie zadań komentarzy** — Skanuj pliki Open Source dla programu vs i zgłoś je w oknie Lista zadań.

- **Wyróżnij pasujące tokeny** — Wyróżnij otaczające nawiasy lub składnię pasujące do miejsca, w którym znajduje się kursor.

## <a name="outlining"></a>Tworzenie konspektu

- **Włącz tworzenie konspektu — umożliwia** wprowadzanie trybu konspektu podczas otwierania pliku.

- **Zakreśl regiony dyrektywy pragma** — automatycznie konspekty `#pragma` bloków regionów.

- **Konspekt bloków instrukcji** — automatyczne konspekty bloków instrukcji.

## <a name="see-also"></a>Zobacz też

- [Ustawianie opcji Edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoryzacja w języku C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
