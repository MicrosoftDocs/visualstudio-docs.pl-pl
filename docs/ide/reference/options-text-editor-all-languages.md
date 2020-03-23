---
title: Opcje, edytor tekstu, wszystkie języki
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9815bdec94ce32a3bfcc170dd95d834bc43ea58f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566881"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Okno dialogowe Opcje: Edytor \> tekstu Wszystkie języki

To okno dialogowe umożliwia zmianę domyślnego zachowania Edytora kodu. Te ustawienia dotyczą również innych edytorów na podstawie Edytora kodu, takich jak widok źródłowy projektanta HTML. Aby otworzyć to okno dialogowe, wybierz **polecenie Opcje** z menu **Narzędzia.** W folderze **Edytor tekstu** rozwiń podfolder **Wszystkie języki,** a następnie wybierz pozycję **Ogólne**.

> [!CAUTION]
> Ta strona ustawia domyślne opcje dla wszystkich języków programowania. Pamiętaj, że zresetowanie opcji w tym oknie dialogowym spowoduje zresetowanie opcji ogólnych we wszystkich językach do wyboru, niezależnie od wybranych w tym miejscu opcji. Aby zmienić opcje edytora tekstu tylko dla jednego języka, rozwiń podfolder dla tego języka i wybierz jego strony opcji.

Wyszarzone znacznik wyboru jest wyświetlany, gdy na stronach opcji ogólnych wybrano opcję dla niektórych języków programowania, ale nie dla innych.

## <a name="statement-completion"></a>Dokańczanie instrukcji

**Automatyczne listy członków**

Po wybraniu tej opcji listy podręczne dostępnych elementów członkowskich, właściwości, wartości lub metod są wyświetlane przez program IntelliSense podczas wpisywania w edytorze. Wybierz dowolny element z listy podręcznej, aby wstawić element do kodu. Wybranie tej opcji powoduje, że opcja **Ukryj elementy zaawansowane.**

**Ukrywanie zaawansowanych członków**

Gdy ta opcja jest zaznaczona, skraca listy uzupełnień zestawienia wyskakującego, wyświetlając tylko te elementy najczęściej używane. Inne elementy są filtrowane z listy.

**Informacje o parametrach**

Po wybraniu tej opcji pełna składnia bieżącej deklaracji lub procedury jest wyświetlana w punkcie wstawiania w edytorze ze wszystkimi dostępnymi parametrami. Następny parametr, który można przypisać, jest wyświetlany pogrubioną czcionką.

## <a name="settings"></a>Ustawienia

**Włącz przestrzeń wirtualną**

Gdy ta opcja jest zaznaczona, a **zawijanie wyrazu** jest wyczyszczone, można kliknąć w dowolnym miejscu poza końcem wiersza w Edytorze kodu i wpisać. Ta funkcja może służyć do umieszczania komentarzy w spójnym punkcie obok kodu.

**Zawijanie**

Gdy ta opcja jest zaznaczona, w następnym wierszu automatycznie wyświetlana jest dowolna część linii, która wykracza poziomo poza widoczny obszar edytora. Wybranie tej opcji umożliwia opcję **Pokaż glify wizualne dla zawijania wyrazów.**

> [!NOTE]
> Funkcja **przestrzeń wirtualna** jest wyłączona, gdy jest włączone **zawijanie wyrazów.**

**Pokaż glify wizualne dla zawijać wyrazów**

Po wybraniu tej opcji wyświetlany jest wskaźnik strzałki powrotnej, w którym długa linia zawija się na drugą linię.

![LineBreakSymbol zrzut ekranu](../../ide/reference/media/linebreak.gif)

Wyczyść tę opcję, jeśli nie chcesz wyświetlać tych wskaźników.

> [!NOTE]
> Te strzałki przypomnienia nie są dodawane do kodu i nie są drukowane. Mają one tylko do celów informacyjnych.

**Numery wierszy**

Po wybraniu tej opcji obok każdego wiersza kodu pojawia się numer wiersza.

> [!NOTE]
> Te numery wierszy nie są dodawane do kodu i nie są drukowane. Mają one tylko do celów informacyjnych.

**Włączanie nawigacji po adresach URL z jednym kliknięciem**

Po wybraniu tej opcji kursor myszy zmienia się w dłoń wskazującą, gdy przechodzi przez adres URL w edytorze. Możesz kliknąć adres URL, aby wyświetlić wskazaną stronę w przeglądarce internetowej.

**Pasek nawigacyjny**

Gdy ta opcja jest zaznaczona, w górnej części edytora kodu zostanie wyświetlony **pasek nawigacyjny.** Jego listy **rozwijane obiekty** i **członkowie** umożliwiają wybranie określonego obiektu w kodzie, wybranie jego członków i przejście do deklaracji wybranego elementu członkowskiego w Edytorze kodu.

**Stosowanie poleceń Wytnij lub Kopiuj do pustych wierszy, gdy nie ma zaznaczenia**

Ta opcja ustawia zachowanie edytora po umieszczeniu punktu wstawiania w pustym wierszu, zaznaczeniu niczego, a następnie kopiowaniu lub wycinaniu.

- Gdy ta opcja jest zaznaczona, pusta linia jest kopiowana lub wycinana. Jeśli następnie wklej, zostanie wstawiony nowy, pusty wiersz.

- Gdy ta opcja jest wyczyszczona, polecenie Wytnij usuwa puste wiersze. Jednak dane w Schowku są zachowywane. W związku z tym jeśli następnie użyjesz polecenia Wklej, zawartość ostatnio skopiowana do Schowka zostanie wklejona. Jeśli nic nie zostało skopiowane wcześniej, nic nie jest wklejane.

To ustawienie nie ma wpływu na kopiowanie lub wycinanie, gdy wiersz nie jest pusty. Jeśli nic nie jest zaznaczone, cała linia jest kopiowana lub wycinana. Jeśli następnie wklej, tekst całego wiersza i jego znak linii końcowej zostaną wklejone.

> [!TIP]
> Aby wyświetlić wskaźniki spacji, kart i końców linii, a tym samym odróżnić wcięte linie od linii całkowicie pustych, wybierz polecenie **Zaawansowane** z menu **Edycja** i wybierz polecenie **Wyświetl biały spację**.

## <a name="see-also"></a>Zobacz też

- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z IntelliSense](../../ide/using-intellisense.md)
