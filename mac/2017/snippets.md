---
title: Wstawki kodu
description: Jak skutecznie korzystać z fragmentów kodu w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 96344b72dd27095f8b9060078112fb767b1338fc
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984811"
---
# <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu, często nazywane _szablonami kodu_, są przydatne do wydajnego programowania, ponieważ umożliwiają wstawianie i edytowanie wstępnie pisanych bloków kodu. Używanie fragmentów kodu może być wygodne do szybkiego dodawania wspólnych wzorców, a nawet do uczenia się nowych wzorców, gdy Deweloper nie ma pewności składni. Dostępne są szablony dla C#języków, F#, HTML, XML, Python i Razor.

W tej sekcji wyjaśniono, jak tworzyć, wstawiać i używać fragmentów kodu.

## <a name="inserting-a-snippet"></a>Wstawianie fragmentu kodu

Istnieją różne sposoby dodawania fragmentów kodu, z których niektóre zostały opisane poniżej:

- **Rozszerzenie karty** &ndash; Rozpocznij wpisywanie nazwy szablonu, wybierz ją z listy i naciśnij klawisz **Tab**, **Aby** ją dodać:

  ![Rozszerzanie karty w kodzie](media/source-editor-image13.png)

- **Przybornik** &ndash; użyć konsoli przybornika, aby wyświetlić listę wszystkich fragmentów kodu. Przeciągnij dowolny szablon z przybornika do poprawnego położenia w kodzie źródłowym:

  [![fragmenty kodu w przyborniku](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Polecenie INSERT templates** &ndash; nie ma obecnie domyślnego zestawu powiązań kluczy na potrzeby wstawiania szablonu. Aby go utworzyć, przejdź do **okna preferencji > programu Visual Studio > powiązania kluczy** i Wyszukaj `template`. Pozwala to na dodawanie odpowiedniego powiązania klucza do pola Edytuj powiązanie, a następnie kliknięcie przycisku **Zastosuj**:

  ![Powstawanie polecenia szablonu](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Tworzenie nowego szablonu

Chociaż istnieje wiele istniejących szablonów w różnych językach, których można użyć i edytować, można również dodać nowe szablony, przechodząc do **> preferencji programu Visual Studio > edytorze tekstu > fragmenty kodu**:

![Wstawanie nowego szablonu](media/source-editor-image12.png)

Naciśnij przycisk **Dodaj** lub **Edytuj** , aby utworzyć lub edytować fragmenty kodu.

## <a name="keywords-in-code-snippets"></a>Słowa kluczowe w fragmentach kodu

Po wstawieniu fragmentu kodu do edytora wszystkie zdefiniowane słowa kluczowe są wyróżniane i można je edytować przez tabulację między nimi. Słowa kluczowe zachowują się jak "zmienna" w fragmencie kodu i są definiowane przez umieszczenie znaku dolara `$` przed i po nazwie słowa kluczowego. 

Zostanie wyświetlone okno **Edytuj szablon** , edytując wbudowane fragmenty kodu `prop`. Fragment kodu zawiera dwa słowa kluczowe &ndash; `$type$` i `$name$` &ndash;, które mogą mieć ustawione dalsze właściwości (takie jak domyślna wartość i etykietka narzędzia) po prawej stronie okna:

![Edytuj okno szablonu](media/source-editor-image12z.png)

Następujące pola są używane do definiowania fragmentu kodu:

- **Skrót** &ndash; tekst, który użytkownik wpisze do wstawienia fragmentu kodu.
- Fragmenty kodu &ndash; **grupy** są pogrupowane w menu zawartości fragmentu kodu przy użyciu tej wartości.
- **Opis** &ndash; wyjaśnienie celu fragmentu kodu.
- Funkcja **Mime** &ndash; kontroluje, jakie typy plików są dostępne w fragmencie kodu.
- **Jest rozwiniętym szablonem** &ndash; upewnij się, że jest zaznaczone, aby wstawić fragment kodu do kursora przez wpisanie skrótu.
- **Jest otaczający szablonem** &ndash; zaznacz tę opcję, aby wyświetlić ten skrót w menu **przestrzenny z...** Content (zawartość) w edytorze.
- **Tekst szablonu** &ndash; rzeczywistego fragmentu kodu, który zostanie wstawiony do edytora. Symbole zastępcze słów kluczowych można zdefiniować przez otoczenie tokenu ze znakami dolara. `$type$`.
- **Panel właściwości słowa kluczowego** &ndash; po prawej stronie okna, Użyj listy rozwijanej u góry, aby wybrać słowo kluczowe (EG `type`) i edytować właściwości, takie jak wartość domyślna i etykietka narzędzia.

## <a name="using-keywords-in-the-editor"></a>Używanie słów kluczowych w edytorze

Aby użyć wstawki ze słowami kluczowymi, takimi jak zdefiniowane powyżej, wpisz skrót i naciśnij klawisz **Tab** dwa razy, a zawartość wstawki zostanie wstawiona przy kursorze:

![Wstawiono fragment kodu zawierający słowa kluczowe](media/source-editor-image12a.png)

Naciśnij klawisz **Tab** , aby przejść między `object` i `MyProperty`, aby dostosować fragment kodu dla klasy.

Słowo kluczowe może być powtórzone w fragmencie kodu, takim jak `for` przykład, Zauważ, że `$i$` słowo kluczowe pojawia się 3 razy:

![Szablon fragmentu ze powtarzalnymi słowami kluczowymi](media/source-editor-image12b.png)

Gdy jest używany w edytorze, klawisz **Tab** przełączy się między pierwszym `i` i `max`. W przypadku zastępowania `i` z inną nazwą zmiennej wszystkie trzy wystąpienia zostaną zaktualizowane:

![Wstawiono fragment kodu pokazujący wiele słów kluczowych](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Zastrzeżone słowa kluczowe

Istnieją dwa zastrzeżone słowa kluczowe, których można użyć w fragmencie kodu:

- `$selected$` &ndash;, jeśli fragment kodu **jest otoczony** zaznaczeniem szablonu, słowo kluczowe zostanie zastąpione tekstem, który został wyróżniony w edytorze po wybraniu fragmentu kodu.
- `$end$` &ndash;, gdy użytkownik zakończył edytowanie słów kluczowych w fragmencie kodu, kursor zostanie umieszczony w lokalizacji słowa kluczowego `$end$`.

Fragment kodu `for` w poprzedniej sekcji jest przykładem obu tych zarezerwowanych słów kluczowych.

Aby uzyskać więcej informacji, zapoznaj się z tematem [Dokumentacja fragmentów kodu programu Visual Studio](/visualstudio/ide/code-snippets-schema-reference#keywords) .

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu (Visual Studio w systemie Windows)](/visualstudio/ide/code-snippets)