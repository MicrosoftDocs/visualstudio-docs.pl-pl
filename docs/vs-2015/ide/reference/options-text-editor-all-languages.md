---
title: Opcje, Edytor tekstu, wszystkie języki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ebe2da1dec9917a792f3e4e02516a79cff605c80
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662402"
---
# <a name="options-text-editor-all-languages"></a>Opcje, edytor tekstu, wszystkie języki
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

To okno dialogowe umożliwia zmianę domyślnego zachowania edytora kodu. Te ustawienia mają zastosowanie również do innych edytorów w oparciu o Edytor kodu, taki jak widok źródła projektanta HTML. Aby otworzyć to okno dialogowe, wybierz **Opcje** z menu **Narzędzia** . W folderze **Edytor tekstu** rozwiń podfolder **wszystkie języki** , a następnie wybierz pozycję **Ogólne**.

> [!CAUTION]
> Ta strona służy do ustawiania opcji domyślnych dla wszystkich języków deweloperskich. Należy pamiętać, że Resetowanie opcji w tym oknie dialogowym spowoduje zresetowanie opcji ogólnych we wszystkich językach do wybranych opcji. Aby zmienić opcje edytora tekstu dla tylko jednego języka, rozwiń podfolder dla tego języka i wybierz jego strony opcji.

 Szary znacznik wyboru jest wyświetlany po wybraniu opcji na stronach opcji ogólnych dla niektórych języków programowania, ale nie dla innych.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="statement-completion"></a>Dokańczanie instrukcji
 Po wybraniu listy rozwijanej Wyświetlaj listę dostępnych elementów członkowskich, właściwości, wartości lub metody są wyświetlane przez funkcję IntelliSense podczas wpisywania w edytorze. Wybierz dowolny element z listy podręcznej, aby wstawić element do kodu. Wybranie tej opcji powoduje włączenie opcji **Ukryj zaawansowane składowe** .

 Ukryj zaawansowane elementy członkowskie po zaznaczeniu, skraca listy uzupełniania wyskakujących instrukcji, wyświetlając tylko te elementy, które najczęściej są używane. Inne elementy są filtrowane z listy.

 Informacje o parametrach po zaznaczeniu, Pełna składnia dla bieżącej deklaracji lub procedura jest wyświetlana w punkcie wstawiania w edytorze, ze wszystkimi dostępnymi parametrami. Następny parametr, który można przypisać, jest wyświetlany pogrubioną czcionką.

## <a name="settings"></a>Ustawienia
 Włącz wirtualne miejsce, gdy ta opcja jest zaznaczona, a **Zawijanie wierszy** jest wyczyszczone, możesz kliknąć dowolne miejsce poza końcem wiersza w edytorze kodu i wpisać. Ta funkcja może służyć do pozycjonowania komentarzy w spójnym punkcie obok kodu.

 Zawijanie wyrazów po zaznaczeniu, każda część linii, która rozszerza się w poziomie poza widoczny obszar edytora, zostanie automatycznie wyświetlona w następnym wierszu. Wybranie tej opcji powoduje włączenie opcji **Pokaż glify wizualne dla zawijania wyrazów** .

> [!NOTE]
> Funkcja **miejsce wirtualne** jest wyłączona, gdy **Zawijanie wierszy** jest włączone.

 Pokaż symbole wizualne dla zawijania wyrazów po zaznaczeniu, wyświetlany jest wskaźnik strzałki powrotu, w której długi wiersz jest zawijany do drugiego wiersza.

 ![Zrzut ekranu LineBreakSymbol](../../ide/reference/media/linebreak.gif "LineBreak")

 Usuń zaznaczenie tej opcji, jeśli wolisz nie wyświetlać tych wskaźników.

> [!NOTE]
> Te strzałki przypomnień nie są dodawane do kodu i nie są drukowane. Są one przeznaczone tylko do celów informacyjnych.

 Zastosuj polecenia Wytnij lub Kopiuj do pustych wierszy, gdy nie ma zaznaczenia ta opcja ustawia zachowanie edytora po umieszczeniu punktu wstawiania w pustym wierszu, zaznacz opcję Brak, a następnie skopiuj lub Wytnij.

- Gdy ta opcja jest zaznaczona, pusty wiersz jest kopiowany lub obcinany. W przypadku wklejenia zostanie wstawiony nowy pusty wiersz.

- Gdy ta opcja jest wyczyszczona, polecenie Wytnij usuwa puste wiersze. Jednak dane w schowku są zachowywane. W związku z tym, jeśli następnie użyjesz polecenia Wklej, zawartość ostatnio skopiowana do schowka zostanie wklejona. Jeśli nic nie zostało wcześniej skopiowane, nic nie zostanie wklejone.

  To ustawienie nie ma wpływu na kopiowanie lub wycinanie, gdy linia nie jest pusta. Jeśli nic nie jest zaznaczone, cała linia jest kopiowana lub obcinana. Jeśli następnie wklejasz, tekst całego wiersza i jego znaku EndLine zostaną wklejone.

> [!TIP]
> Aby wyświetlić wskaźniki dla spacji, kart i punktów końcowych, a tym samym rozróżnić wcięcia wierszy od wierszy, które są całkowicie puste, wybierz opcję **Zaawansowane** z menu **Edycja** i wybierz opcję **Wyświetl biały znak**.

## <a name="display"></a>Monitor
 Numery wierszy po zaznaczeniu numer wiersza pojawia się obok każdego wiersza kodu.

> [!NOTE]
> Te numery wierszy nie są dodawane do kodu i nie są drukowane. Są one przeznaczone tylko do celów informacyjnych.

 Włącz nawigację URL jednym kliknięciem po zaznaczeniu, kursor myszy zmienia się w wskazanie wskazującej na adres URL w edytorze. Możesz kliknąć adres URL, aby wyświetlić określoną stronę w przeglądarce sieci Web.

 Pasek nawigacyjny po zaznaczeniu wyświetla **pasek nawigacyjny** u góry edytora kodu. Jego listy rozwijane **obiekty** i **elementy członkowskie** umożliwiają wybranie określonego obiektu w kodzie, wybranie z jego członków i przejście do deklaracji wybranego elementu członkowskiego w edytorze kodu.

## <a name="see-also"></a>Zobacz też
 [Opcje, Edytor tekstu, wszystkie języki, karty](../../ide/reference/options-text-editor-all-languages-tabs.md) [Ogólne, środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md) [przy użyciu technologii IntelliSense](../../ide/using-intellisense.md)
