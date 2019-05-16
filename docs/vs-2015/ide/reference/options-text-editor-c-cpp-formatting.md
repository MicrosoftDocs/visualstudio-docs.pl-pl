---
title: Opcje, Edytor tekstu, C-C++, formatowanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 66adcdeca1aa794649b42f4ae153d9b2f879deff
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697137"
---
# <a name="options-text-editor-cc-formatting"></a>Opcje, edytor tekstu, C/C++, formatowanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pozwala zmienić domyślne zachowanie Edytora kodu podczas programowania w C lub C++.  
  
 Dostępu do tej strony, w **opcje** rozwiń w lewym okienku w oknie dialogowym **edytora tekstów**, rozwiń węzeł **C/C++**, a następnie kliknij przycisk **formatowanie** .  
  
> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="cc-options"></a>Opcje C/C++  
 **Włącz automatyczne etykietki narzędzi z szybkie informacje**  
 Włącza lub wyłącza funkcję Szybkie informacje technologii IntelliSense.  
  
## <a name="inactive-code"></a>Kod nieaktywny  
 **Pokaż bloków nieaktywnego kodu**  
 Kod, który jest nieaktywny ze względu na `#ifdef` deklaracji jest pokolorowany inaczej, aby ułatwić jego identyfikację.  
  
 **Wyłącz nieprzezroczystość nieaktywnego kodu**  
 Nieaktywny kod można zidentyfikować za pomocą kolorów zamiast przezroczystości.  
  
 **Procent krycia nieaktywnego kodu**  
 Można dostosować stopień krycia dla bloków nieaktywnego kodu.  
  
## <a name="indentation"></a>Wcięcie  
 **Wcięcie nawiasów klamrowych**  
 Można skonfigurować sposób wyrównania nawiasów klamrowych po naciśnięciu klawisza ENTER, gdy użytkownik rozpocznie blok kodu, na przykład funkcję lub a `for` pętli. Nawiasy klamrowe mogą być wyrównane względem pierwszego znaku bloku kodu lub wcięte.  
  
 **Automatyczne wcięcie na karcie**  
 Można skonfigurować, co się dzieje w bieżącym wierszu kodu po naciśnięciu klawisza TAB. Albo wiersz zostaje wcięty, albo zostaje wstawiony tabulator.  
  
## <a name="miscellaneous"></a>Różne  
 **Wylicz komentarze w oknie Lista zadań**  
 Edytor może skanować otwarte pliki źródłowe pod kątem wstępnie określonych słów w komentarzach. Tworzy wpis w **listy zadań** okna dla dowolnego słowa kluczowego, które znajdzie.  
  
 **Podświetl pasujące tokeny**  
 Gdy kursor znajduje się obok nawiasu klamrowego, edytor może wyróżnić pasujący nawias klamrowy, abyś mógł łatwiej wyróżnić odpowiedni kod.  
  
## <a name="outlining"></a>Tworzenie konspektu  
 **Przejdź do trybu konspektu po otwarciu plików**  
 Po przywróceniu pliku do edytora tekstów można włączyć funkcję tworzenia konspektów. Aby uzyskać więcej informacji, zobacz [konspekt](../../ide/outlining.md). Gdy ta opcja jest zaznaczona, tworzenie konspektów jest włączone po otwarciu pliku.  
  
 **Automatyczne tworzenie konspektu bloków regionu #pragma**  
 Kiedy ta opcja jest zaznaczona, automatyczne tworzenie konspektu dla [dyrektyw pragma](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) jest włączona. Dzięki temu można rozwinąć lub zwinąć bloki regionów pragmy w trybie konspektu.  
  
 **Automatyczny konspekt bloków instrukcji**  
 Kiedy ta opcja jest zaznaczona, automatyczne tworzenie konspektu jest włączone dla następujących konsruktów instrukcji:  
  
- [if-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)  
  
- [switch, instrukcja (C++)](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)  
  
- [while, instrukcja (C++)](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne, środowisko, okno dialogowe Opcje](../../ide/reference/general-environment-options-dialog-box.md)   
 [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)
