---
title: Wstawki kodu
description: Jak skutecznie programować w programie Visual Studio dla komputerów Mac za pomocą urywków kodu
author: cobey
ms.author: cobey
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 1dacc935549d738ff1b5e84c3ac4420c343155fd
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "68787697"
---
# <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu, często określane jako _szablony kodu,_ są przydatne do efektywnego programowania, ponieważ umożliwiają wstawianie i edytowanie wstępnie napisanych bloków kodu. Za pomocą fragmentów kodu może być wygodne do szybkiego dodawania typowych wzorców, a nawet do uczenia się nowych wzorców, gdy jako deweloper nie masz pewności składni. Istnieją szablony dla języka C#, F#, HTML, XML, Python i Razor.

W tej sekcji wyjaśniono, jak tworzyć, wstawiać i używać urywków w kodzie.

## <a name="inserting-a-snippet"></a>Wstawianie fragmentu kodu

Istnieje kilka różnych sposobów dodawania fragmentów kodu, z których niektóre są opisane poniżej:

- **Rozszerzenie karty** &ndash; Zacznij wpisywać nazwę szablonu, zaznacz ją z listy i naciśnij **klawisz Tab**, **Tab,** aby ją dodać:

  ![Rozszerzenie karty w kodzie](media/source-editor-image13.png)

- **Przybornik** &ndash; Użyj przybornika, aby wyświetlić listę wszystkich fragmentów kodu. Przeciągnij dowolny szablon z przybornika do właściwej pozycji w kodzie źródłowym:

  [![Urywki kodu w przyborniku](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Polecenie** &ndash; Wstaw szablony Obecnie nie ma domyślnego zestawu powiązań klawiszy do wstawiania szablonu. Aby go utworzyć, przejdź do **programu Visual Studio > preferencje > powiązaniami klawiszy** i wyszukaj program `template`. Umożliwia to dodanie żądanego powiązania klucza do pola Edytuj powiązanie, a następnie kliknij przycisk **Zastosuj:**

  ![Polecenie Szablon wstawki](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Tworzenie nowego szablonu

Chociaż istnieje wiele istniejących szablonów w różnych językach, których można używać i edytować, nowe szablony można również dodać, przechodząc do **programu Visual Studio > Preferences > Text Editor > urywki kodu:**

![Nowy szablon wstawki](media/source-editor-image12.png)

Naciśnij **przyciski Dodaj** lub **Edytuj,** aby utworzyć lub edytować fragmenty kodu.

## <a name="keywords-in-code-snippets"></a>Słowa kluczowe we fragmentach kodu

Po wstawieniu fragmentu kodu do edytora wszystkie zdefiniowane słowa kluczowe są podświetlane i mogą być edytowane przez tabulatora między nimi. Słowa kluczowe zachowują się jak "zmienna" we weszło w fragment `$` kodu i są definiowane przez umieszczenie znaku dolara przed i po nazwie słowa kluczowego. 

Poniżej zostanie wyświetlone okno **Edytuj szablon,** edytując wbudowany `prop` fragment kodu. Fragment kodu zawiera dwa słowa &ndash; `$type$` `$name$` &ndash; kluczowe, które mogą mieć ustawione dalsze właściwości (takie jak wartość domyślna i etykietka narzędzia) po prawej stronie okna:

![Okno edytowania szablonu](media/source-editor-image12z.png)

Do zdefiniowania fragmentu kodu używane są następujące pola:

- **Skrót** &ndash; Tekst, który użytkownik wpisuje, aby wstawić fragment kodu.
- Urywki **grupy** &ndash; są zgrupowane w menu zawartości fragmentu kodu przy użyciu tej wartości.
- **Opis** &ndash; Wyjaśnienie celu fragmentu kodu.
- **Mime** &ndash; Kontroluje typy plików, w jakich są dostępne urywki.
- **Jest szablonem rozwijanym** &ndash; Upewnij się, że jest to zaznaczone, aby fragment kodu można było wstawić na kursorze, wpisując skrót.
- **Jest otoczyć z szablonem** &ndash; Sprawdź tę opcję, aby wyświetlić ten skrót w menu **Surround z...** zawartością w edytorze.
- **Tekst** &ndash; szablonu Rzeczywisty fragment kodu, który zostanie wstawiony do edytora. Symbole zastępcze słów kluczowych można zdefiniować poprzez otoczenie tokenu ze znakami dolara np. `$type$`.
- **Panel** &ndash; właściwości słowa kluczowego Po prawej stronie okna użyj listy rozwijanej u góry, aby wybrać słowo kluczowe (np. `type`) i edytować właściwości, takie jak wartość domyślna i etykietka narzędzia.

## <a name="using-keywords-in-the-editor"></a>Używanie słów kluczowych w edytorze

Aby użyć fragmentu ze słowami kluczowymi, takimi jak zdefiniowany powyżej, wpisz skrót i naciśnij dwukrotnie **klawisz Tab,** a zawartość fragmentu kodu zostanie wstawiona na kursorze:

![Wstawiony fragment kodu przedstawiający słowa kluczowe](media/source-editor-image12a.png)

Naciśnij klawisz **Tab,** `object` aby `MyProperty` przejść między i dostosować fragment kodu dla swojej klasy.

Słowo kluczowe można powtórzyć we we wemieć, na przykład w tym `for` przykładzie, zwróć uwagę, `$i$` że słowo kluczowe pojawia się 3 razy:

![Szablon urywka z powtarzającymi się słowami kluczowymi](media/source-editor-image12b.png)

Gdy jest używany w **Tab** edytorze, klawisz `i` Tab `max`przełącza się między pierwszym i . Jeśli wpiszesz `i` nazwę innej zmiennej, wszystkie trzy wystąpienia zostaną zaktualizowane:

![Wstawiony fragment kodu przedstawiający wiele słów kluczowych](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Zastrzeżone słowa kluczowe

Istnieją dwa zastrzeżone słowa kluczowe, których można użyć we we wemieciach:

- `$selected$`&ndash; Jeśli fragment kodu **jest otoczony z zaznaczonym szablonem,** to słowo kluczowe zostanie zastąpione tekstem, który został wyróżniony w edytorze po wybraniu fragmentu kodu.
- `$end$`&ndash; Po zakończeniu edytowania słów kluczowych przez użytkownika w urywce kursor zostanie umieszczony `$end$` w lokalizacji słowa kluczowego.

Fragment `for` kodu w poprzedniej sekcji jest przykładem obu tych zarezerwowanych słów kluczowych.

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu (Visual Studio w systemie Windows)](/visualstudio/ide/code-snippets)
