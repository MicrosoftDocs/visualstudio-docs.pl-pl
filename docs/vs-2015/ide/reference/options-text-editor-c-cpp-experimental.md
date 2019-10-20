---
title: Opcje, Edytor tekstu, C-C++, eksperymentalne | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7e9d1464481b33bc5fbf5e73bc09a6da4eb082c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662346"
---
# <a name="options-text-editor-cc-experimental"></a>Opcje, Edytor tekstów, C/C++, eksperymentalne
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zmieniając te opcje, można zmienić zachowanie związane z technologią IntelliSense i bazą danych przeglądania podczas programowania w języku C lub C++.

 Aby uzyskać dostęp do tej strony, w oknie dialogowym **Opcje** w okienku po lewej stronie rozwiń pozycję **Edytor tekstu**, rozwiń węzeł **CC++/** , a następnie wybierz pozycję **eksperymentalne**.

 Te funkcje są dostępne w instalacji programu Visual Studio 2015 Update 1 RC.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Przeglądanie/Nawigacja
 **Włącz nowy aparat bazy danych** Powinno to spowodować automatyczną przyspieszenie wypełniania bazy danych i szybsze wykonywanie wszystkich operacji w bazie danych (bez dokładności) dla operacji takich jak **Przejdź do definicji** i **Znajdź wszystkie odwołania**. (Po prostu Zamknij i ponownie otwórz rozwiązanie, aby zastosować zmiany; nie musisz ponownie uruchamiać programu Visual Studio).

## <a name="intellisense"></a>IntelliSense
 **Lista elementów członkowskich z kropką na strzałkę** Zastępuje znak "." elementem "->", jeśli jest to możliwe dla listy elementów członkowskich.

## <a name="refactoring"></a>Refaktoryzacja
 **Włącz funkcję Extract** Wyodrębnij zaznaczony kod do jego własnej funkcji i Zastąp kod wywołaniem nowej funkcji. Aby uzyskać dostęp do tej funkcji, kliknij prawym przyciskiem myszy wybrany kod i wybierz polecenie **szybkie akcje**lub po prostu naciśnij skrót domyślny Ctrl + kropka [Ctrl +.].

 **Włącz zmianę sygnatury** Dodawanie, zmienianie kolejności i usuwanie parametrów funkcji i propagowanie zmian do wszystkich witryn wywołań. Aby uzyskać dostęp do tej funkcji, kliknij prawym przyciskiem myszy dowolne użycie funkcji i wybierz polecenie **szybkie akcje**lub po prostu naciśnij skrót domyślny Ctrl + kropka [Ctrl +.].

## <a name="text-editor"></a>Edytor tekstu
 **Włącz rozwijanie zakresów** Jeśli ta funkcja jest włączona, można ująć zaznaczony tekst za pomocą nawiasów klamrowych, wpisując "{" w edytorze tekstu.

 **Włącz pierwszeństwo rozwijania** Jeśli ta funkcja jest włączona, można ująć zaznaczony tekst za pomocą nawiasów, wpisując znak "(" w edytorze tekstu.

 Aby uzyskać dodatkowe funkcje edytora tekstu w galerii programu Visual Studio, zapoznaj się z listą [tutaj](http://go.microsoft.com/fwlink/?LinkId=692016). Przykładem są [ C++ szybkie poprawki](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), które obsługują następujące rozwiązania:

- **Dodaj brakujące #include** -proponuje odpowiednie #include dla nieznanych symboli w kodzie

- **Dodaj przy użyciu przestrzeni nazw/w pełni kwalifikujących się symboli** — podobnie jak w przypadku poprzedniego elementu, ale dla przestrzeni nazw

- **Dodaj brakujący średnik**

- **Pomoc MSDN** — wyszukiwanie komunikatów o błędach w witrynie MSDN

  Możesz umieścić kursor na zygzaku, aby uzyskać żarówkę, lub użyć domyślnego skrótu klawiaturowego Ctrl + kropka (Ctrl +.). Należy pamiętać, że w przypadku skrótu klawiaturowego karetka nie musi być umieszczona w określonym błędzie lub tokenie; Możesz po prostu znajdować się w tym samym wierszu, w którym wystąpił błąd, aby wywoływać sugestie dla wszystkiego w tym wierszu.

## <a name="see-also"></a>Zobacz też
 [Ustawienie refaktoryzacji opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md) [ C++ (blog VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
