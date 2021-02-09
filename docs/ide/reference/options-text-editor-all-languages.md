---
title: Opcje, edytor tekstu, wszystkie języki
description: Dowiedz się, jak za pomocą strony Ogólne w sekcji wszystkie języki zmienić domyślne zachowanie edytora kodu w programie Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b507f79aa4afb1bd5d2f56893d2e32aae0db4c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905578"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Opcje — okno dialogowe: Edytor tekstu — \> wszystkie języki

To okno dialogowe umożliwia zmianę domyślnego zachowania edytora kodu. Te ustawienia mają zastosowanie również do innych edytorów w oparciu o Edytor kodu, taki jak widok źródła projektanta HTML. Aby otworzyć to okno dialogowe, wybierz **Opcje** z menu **Narzędzia** . W folderze **Edytor tekstu** rozwiń podfolder **wszystkie języki** , a następnie wybierz pozycję **Ogólne**.

> [!CAUTION]
> Ta strona służy do ustawiania opcji domyślnych dla wszystkich języków deweloperskich. Należy pamiętać, że Resetowanie opcji w tym oknie dialogowym spowoduje zresetowanie opcji ogólnych we wszystkich językach do wybranych opcji. Aby zmienić opcje edytora tekstu dla tylko jednego języka, rozwiń podfolder dla tego języka i wybierz jego strony opcji.

Szary znacznik wyboru jest wyświetlany po wybraniu opcji na stronach opcji ogólnych dla niektórych języków programowania, ale nie dla innych.

## <a name="statement-completion"></a>Dokańczanie instrukcji

**Autolista członków**

Po wybraniu listy podręczne dostępne elementy członkowskie, właściwości, wartości lub metody są wyświetlane przez funkcję IntelliSense podczas wpisywania w edytorze. Wybierz dowolny element z listy podręcznej, aby wstawić element do kodu. Wybranie tej opcji powoduje włączenie opcji **Ukryj zaawansowane składowe** .

**Ukryj zaawansowane elementy członkowskie**

Gdy jest zaznaczone, skraca listy uzupełniania wyskakujących instrukcji, wyświetlając tylko te elementy, które są najczęściej używane. Inne elementy są filtrowane z listy.

**Informacje o parametrach**

Po wybraniu Pełna składnia dla bieżącej deklaracji lub procedury jest wyświetlana w punkcie wstawiania w edytorze, ze wszystkimi dostępnymi parametrami. Następny parametr, który można przypisać, jest wyświetlany pogrubioną czcionką.

## <a name="settings"></a>Ustawienia

**Włącz wirtualne miejsce**

Gdy ta opcja jest zaznaczona, a **Zawijanie** wierszy jest wyczyszczone, można kliknąć dowolne miejsce poza końcem wiersza w edytorze kodu i wpisać. Ta funkcja może służyć do pozycjonowania komentarzy w spójnym punkcie obok kodu.

**Zawijanie wierszy**

Po wybraniu każda część linii, która rozszerza się w poziomie poza widoczny obszar edytora, zostanie automatycznie wyświetlona w następnym wierszu. Wybranie tej opcji powoduje włączenie opcji **Pokaż glify wizualne dla zawijania wyrazów** .

> [!NOTE]
> Funkcja **miejsce wirtualne** jest wyłączona, gdy **Zawijanie wierszy** jest włączone.

**Pokaż symbole wizualne dla zawijania wierszy**

Po wybraniu wskaźnik strzałki powrotu jest wyświetlany, gdy długa linia jest zawijana do drugiego wiersza.

![Zrzut ekranu LineBreakSymbol](../../ide/reference/media/linebreak.gif)

Usuń zaznaczenie tej opcji, jeśli wolisz nie wyświetlać tych wskaźników.

> [!NOTE]
> Te strzałki przypomnień nie są dodawane do kodu i nie są drukowane. Są one przeznaczone tylko do celów informacyjnych.

**Numery wierszy**

Po wybraniu numer wiersza pojawia się obok każdego wiersza kodu.

> [!NOTE]
> Te numery wierszy nie są dodawane do kodu i nie są drukowane. Są one przeznaczone tylko do celów informacyjnych.

**Włącz nawigację adresów URL jednym kliknięciem**

Po zaznaczeniu kursor myszy zmieni się w wskazanie wskazujące adres URL w edytorze. Możesz kliknąć adres URL, aby wyświetlić określoną stronę w przeglądarce sieci Web.

**Pasek nawigacyjny**

Po wybraniu Wyświetla **pasek nawigacyjny** u góry edytora kodu. Jego listy rozwijane **obiekty** i **elementy członkowskie** umożliwiają wybranie określonego obiektu w kodzie, wybranie z jego członków i przejście do deklaracji wybranego elementu członkowskiego w edytorze kodu.

**Zastosuj polecenia Wytnij lub Kopiuj do pustych wierszy, gdy nie ma zaznaczenia**

Ta opcja ustawia zachowanie edytora po umieszczeniu punktu wstawiania w pustym wierszu, zaznacz opcję Brak, a następnie skopiuj lub Wytnij.

- Gdy ta opcja jest zaznaczona, pusty wiersz jest kopiowany lub obcinany. W przypadku wklejenia zostanie wstawiony nowy pusty wiersz.

- Gdy ta opcja jest wyczyszczona, polecenie Wytnij usuwa puste wiersze. Jednak dane w schowku są zachowywane. W związku z tym, jeśli następnie użyjesz polecenia Wklej, zawartość ostatnio skopiowana do schowka zostanie wklejona. Jeśli nic nie zostało wcześniej skopiowane, nic nie zostanie wklejone.

To ustawienie nie ma wpływu na kopiowanie lub wycinanie, gdy linia nie jest pusta. Jeśli nic nie jest zaznaczone, cała linia jest kopiowana lub obcinana. Jeśli następnie wklejasz, tekst całego wiersza i jego znaku EndLine zostaną wklejone.

> [!TIP]
> Aby wyświetlić wskaźniki dla spacji, kart i punktów końcowych, a tym samym rozróżnić wcięcia wierszy od wierszy, które są całkowicie puste, wybierz opcję **Zaawansowane** z menu **Edycja** i wybierz opcję **Wyświetl biały znak**.

## <a name="see-also"></a>Zobacz też

- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)
