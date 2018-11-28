---
title: Opcje, edytor tekstu, wszystkie języki
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fa208805a8d6861082793551dbbc595985fdc55
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52387991"
---
# <a name="options-text-editor-all-languages"></a>Opcje, edytor tekstu, wszystkie języki

To okno dialogowe pozwala zmienić domyślne zachowanie edytora kodu. Te ustawienia mają zastosowanie również do innych edytorów oparte na kod edytora, takiego jak widok źródła w Projektancie HTML. Aby otworzyć to okno dialogowe, wybierz **opcje** z **narzędzia** menu. W ramach **edytora tekstów** folder, rozwiń węzeł **wszystkie języki** podfolder, a następnie wybierz **ogólne**.

> [!CAUTION]
> Ta strona ustawia domyślne opcje dla wszystkich języków programowania. Należy pamiętać, że zresetowanie opcji, w tym oknie dialogowym przywróci ogólne opcje we wszystkich językach niezależnie od opcji wybranych są w tym miejscu. Aby zmienić opcje edytora tekstowego dla tylko jednego języka, rozwiń podfolder dla danego języka, a następnie wybierz jego stron opcji.

Wygaszone znacznik wyboru jest wyświetlane, gdy po wybraniu opcji na stronach opcji ogólnych dla niektórych języków programowania, ale nie dla innych użytkowników.

## <a name="statement-completion"></a>Dokańczanie instrukcji

**Automatyczna lista członków**

Po wybraniu wyskakującego listy dostępne elementy członkowskie, właściwości, wartości lub metody są wyświetlane przez technologię IntelliSense podczas wpisywania w edytorze. Wybierz dowolny element z wyskakującej listy do podawania pozycji w kodzie. Wybranie tej opcji umożliwia **kryj składowe zaawansowane** opcji.

**Kryj składowe zaawansowane**

Po wybraniu skraca uzupełniania instrukcji wyskakujące, wyświetlając tylko te elementy, które są używane najczęściej. Inne elementy są odfiltrowywane z listy.

**Informacje o parametrach**

Po wybraniu pełną składnię bieżącej deklaracji lub procedura jest wyświetlana w obszarze punkt wstawiania w edytorze, ze wszystkimi jego dostępnych parametrów. Następny parametr, które można przypisać jest wyświetlany czcionką pogrubioną.

## <a name="settings"></a>Ustawienia

**Włączyć wirtualną przestrzeń**

Gdy ta opcja jest zaznaczona i **zawijanie wyrazów** jest wyczyszczone, można kliknąć dowolne miejsce poza końcem wiersza w edytorze kodu i typu. Ta funkcja może służyć do pozycji Komentarze w momencie spójne obok kodu.

**Zawijanie wyrazów**

Po wybraniu dowolnej części wiersza, który mieści się w poziomie w obszarze edytora w widoczne jest automatycznie wyświetlana w następnym wierszu. Wybranie tej opcji umożliwia **Pokaż zualne przy zawijaniu wierszy** opcji.

> [!NOTE]
> **Wirtualną przestrzenią** włączenia funkcji wyłączone podczas **zawijanie** znajduje się na.

**Pokaż zualne przy zawijaniu wierszy**

Po wybraniu wskaźnik zwracany strzałkę jest wyświetlany, gdy długi wiersz zawijana drugi wiersz.

![LineBreakSymbol — zrzut ekranu](../../ide/reference/media/linebreak.gif)

Usuń zaznaczenie tej opcji, jeśli nie chcesz wyświetlić te wskaźniki.

> [!NOTE]
> Tych strzałek monitu nie są dodawane do kodu, a nie do drukowania. Są one tylko do celów referencyjnych.

**Numery wierszy**

Po wybraniu numer wiersza obok każdego wiersza kodu.

> [!NOTE]
> Te numery wierszy nie są dodawane do kodu, a nie do drukowania. Są one tylko do celów referencyjnych.

**Włącz nawigację adresów URL jednym kliknięciem**

Po wybraniu myszy przybiera postać dłoni przekazywanego za pośrednictwem adresu URL w edytorze. Możesz kliknąć adres URL, aby wyświetlić stronę wskazany w przeglądarce sieci web.

**Pasek nawigacyjny**

Po wybraniu Wyświetla **pasek nawigacyjny** w górnej części edytora kodu. Jego listy rozwijanej **obiektów** i **członków** list pozwalają na wybranie określonego obiektu w kodzie, wybierz jedną z jej członków i przechodzi do deklaracji wybranego elementu członkowskiego w edytorze kodu.

**Zastosuj poleceń Wytnij lub Kopiuj do pustych wierszy, jeśli nie zaznaczono żadnego fragmentu**

Ta opcja ustawia zachowanie edytora, gdy umieścisz kursor w pustym wierszu, wybierz nothing, a następnie skopiować lub wyciąć.

-   Po wybraniu tej opcji pusty wiersz jest skopiować lub wyciąć. Jeśli następnie wkleić, jest wstawiany nowy, pusty wiersz.

-   Gdy ta opcja jest wyczyszczone, polecenie Cut usuwa pustych wierszy. Jednak dane w Schowku jest zachowywana. W związku z tym Jeśli następnie użyć polecenia Wklej, zostanie wklejony zawartości ostatnio skopiowana do Schowka. Jeśli nic nie został skopiowany wcześniej, nic nie zostanie wklejony.

To ustawienie nie ma wpływu na Kopiuj lub Wytnij gdy wiersz nie jest pusty. Jeśli nic nie jest zaznaczone, cały wiersz jest skopiować lub wyciąć. Jeśli następnie wkleić, tekst cały wiersz i jej znak endline zostaną wklejone.

> [!TIP]
> Aby wyświetlić wskaźniki dla miejsca do magazynowania oraz o końców linii, a zatem odróżnienia wiersze z wcięciami wiersze, które są całkowicie pusty, wybierz **zaawansowane** z **Edytuj** menu i wybierz polecenie **widoku biały Miejsce**.

## <a name="see-also"></a>Zobacz też

- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)