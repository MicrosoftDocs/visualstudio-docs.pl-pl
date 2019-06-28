---
title: Wstawki kodu
description: Jak program wydajnie w programie Visual Studio dla komputerów Mac za pomocą fragmentów kodu
author: conceptdev
ms.author: crdun
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: b94a16fbd210bb229881d46071f24c59aea8419e
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465144"
---
# <a name="code-snippets"></a>Fragmenty kodu

Fragmenty, często nazywane kodu _kodu szablonów_, są przydatne w przypadku wydajne programowanie, ponieważ umożliwiają one wstawiania i edytowanie wstępnie napisana bloków kodu. Za pomocą fragmentów kodu może być wygodne do szybkiego dodawania typowych wzorców, lub nawet w przypadku nauki nowych wzorców, gdy deweloper wiesz składni. Istnieją szablony przewidziane C#, F#, HTML, XML, Python i Razor.

W tej sekcji wyjaśniono, jak utworzyć, wstawić i używanie fragmentów kodu w kodzie.

## <a name="inserting-a-snippet"></a>Wstawianie fragmentu kodu

Istnieje kilka różnych sposobów dodawanie fragmentów kodu, z których niektóre są opisane poniżej:

- **Karta rozszerzenia** &ndash; zacznij wpisywać nazwę szablonu, wybierz ją z listy i kliknij **kartę**, **kartę** go dodać:

  ![Rozszerzenia karty w kodzie](media/source-editor-image13.png)

- **Przybornik** &ndash; wyświetlić listę wszystkich fragmentów kodu za pomocą konsoli do przybornika. Przeciągnij dowolny szablon z przybornika do właściwych miejscach w kodzie źródłowym:

  [![Fragmenty kodu w przyborniku](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Wstaw polecenie Szablony** &ndash; klucz nie istnieje obecnie domyślnego powiązania zestawu do wstawiania szablonu. Aby go utworzyć, przejdź do **programu Visual Studio > Preferencje > klucz powiązania** i wyszukaj `template`. Dzięki temu, dodając odpowiednią powiązanie klucza w polu Edytuj powiązania, kliknij przycisk **Zastosuj**:

  ![Polecenie szablonu krawędziowe](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Tworzenie nowego szablonu

Dostępnych jest wiele istniejących szablonów w różnych językach, których można używać i edytować, nowe szablony mogą być również dodawane, przechodząc do **programu Visual Studio > Preferencje > Edytor tekstu > fragmenty kodu**:

![Nowy szablon krawędziowe](media/source-editor-image12.png)

Naciśnij klawisz **Dodaj** lub **Edytuj** przyciski do tworzenia lub edytowania fragmentów kodu.

## <a name="keywords-in-code-snippets"></a>Słowa kluczowe fragmenty kodu

Po wstawieniu fragmentu kodu w edytorze, wszelkie słowa kluczowe zdefiniowane są zaznaczone i mogą być edytowane przez przełączania się między nimi. Słowa kluczowe zachowują się jak "Zmienna" we fragmencie kodu i są definiowane przez umieszczenie znak dolara `$` przed i po nazwie słowa kluczowego. 

**Edytuj szablon** okna jest pokazany poniżej i edytowania wbudowanej `prop` fragmentu kodu. Fragment kodu zawiera dwa słowa kluczowe &ndash; `$type$` i `$name$` &ndash; która może zawierać więcej zbioru (np. domyślna wartość i etykietek narzędzi) po prawej stronie okna właściwości:

![Edytuj okno Szablon](media/source-editor-image12z.png)

Następujące pola są używane do definiowania fragment kodu:

- **Skrót** &ndash; tekst użytkownik wpisuje do wstawiania fragmentu kodu.
- **Grupa** &ndash; fragmenty są zgrupowane razem w menu zawartości fragmentu kodu przy użyciu tej wartości.
- **Opis** &ndash; wyjaśnienie przeznaczenia ten fragment kodu.
- **MIME** &ndash; kontroluje, jakie typy plików jest dostępna w tym fragmencie kodu.
- **Szablon można rozwijać** &ndash; upewnij się, ta opcja zostanie zaznaczona, aby fragment można wstawić przy kursorze, wpisując skrótu.
- **Otocz za pomocą szablonu jest** &ndash; zaznacz tę opcję, aby wyświetlić listę ten skrót **Otocz przez...**  menu zawartości w edytorze.
- **Tekst szablonu** &ndash; rzeczywisty fragment kodu, który zostanie wstawiony do edytora. Symbole zastępcze — słowo kluczowe mogą być definiowane przez umieszczenie token z dolara, np. `$type$`.
- **Panel właściwości — słowo kluczowe** &ndash; na stronie po prawej stronie okna, użyj listy rozwijanej w górnej wybrać słowo kluczowe (np `type`) i edytowanie właściwości, takie jak wartości domyślnej i etykietek narzędzi.

## <a name="using-keywords-in-the-editor"></a>Przy użyciu słów kluczowych w edytorze

Za pomocą fragment słów kluczowych, takich jak ten zdefiniowany powyżej, wpisz skrót, a następnie naciśnij klawisz **kartę** dwa razy, i zawartość fragment kodu zostanie wstawiony na kursora:

![Wstawiono fragment przedstawiający słów kluczowych](media/source-editor-image12a.png)

Naciśnij klawisz **kartę** klawisz, aby przejść między `object` i `MyProperty` dostosować fragment kodu dla swojej klasy.

Słowo kluczowe, które można powtarzać we fragmencie, na przykład to `for` przykładzie należy zauważyć `$i$` — słowo kluczowe pojawia się 3 razy:

![Szablon fragmentu kodu przy użyciu powtarzanych słów kluczowych](media/source-editor-image12b.png)

Gdy jest używana w edytorze **kartę** klucz będzie przełączać się między pierwszym `i` i `max`. Jeśli użytkownik zastępowania `i` pod inną nazwą zmiennej, wszystkie jego wystąpienia zostaną zaktualizowane:

![Wstawiono fragment przedstawiający wiele słów kluczowych](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Zastrzeżone słowa kluczowe

Istnieją dwa zastrzeżonych słów kluczowych, używanych w fragment:

- `$selected$` &ndash; Jeśli ten fragment kodu zawiera **jest Otocz za pomocą szablonu** opcja jest zaznaczona, to słowo kluczowe zostanie zastąpiony tekst, który został wyróżniony w edytorze, gdy wybrano fragmentu kodu.
- `$end$` &ndash; Gdy użytkownik zakończył edycję słowa kluczowe fragmentu kodu, kursor zostanie umieszczona w lokalizacji `$end$` — słowo kluczowe.

`for` Fragment kodu w poprzedniej sekcji to przykład oba te zastrzeżonych słów kluczowych.

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu (Visual Studio Windows)](/visualstudio/ide/code-snippets)