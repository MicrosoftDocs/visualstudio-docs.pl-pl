---
title: Przybornik, karta HTML
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 420a65fb8b91495c5fbba228e190b5589019c99f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576977"
---
# <a name="toolbox-html-tab"></a>Przybornik, karta HTML

**HTML** karta w przyborniku zawiera składniki, które przydają się na stronach sieci web i formularzy sieci web. Aby wyświetlić tę kartę, należy najpierw otworzyć dokument do edycji w Projektancie HTML. Na **widoku** menu, kliknij przycisk **przybornika**, a następnie kliknij przycisk **HTML** kartę przybornika.

 Aby utworzyć wystąpienie narzędzia na **HTML** kartę, albo kliknij dwukrotnie narzędzie, aby dodać go do dokumentu w bieżącym punkcie wstawiania lub wybierz narzędzie i przeciągnij go do żądanej pozycji na powierzchni edycji.

## <a name="ui-elements"></a>Elementy interfejsu użytkownika

Następujące narzędzia są dostępne na karcie HTML domyślnie.

**Pointer**

![ASP.NET Mobile Designer HTMLpage Pointer](../../ide/reference/media/vxpointer.gif)

To narzędzie jest domyślnie zaznaczona, po otwarciu dowolnej karcie przybornika. Nie można usunąć. Wskaźnik umożliwia przeciągnij obiekty na powierzchni projektowej widoku, zmieniać ich rozmiar i zmiany ich położenia na stronie lub formularza. Aby uzyskać więcej informacji, zobacz [przybornika](../../ide/reference/toolbox.md).

**Dane wejściowe (przycisk)**

![Przycisk strony internetowej HTML](../../ide/reference/media/vxbutton.gif)

Wstawia `input` elementu `type="button"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Button1"` jest wstawiany za pierwszy przycisk `id="Button2"` dla drugiej i tak dalej.

Podczas przeciągania **dane wejściowe (przycisk)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Dane wejściowe (Resetowanie)**

![HTMLpageResetButton — zrzut ekranu](../../ide/reference/media/vxreset.gif)

Wstawia `input` elementu `type="reset"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Reset1"` dodaje się do pierwszego przycisku, resetowania `id="Reset2"` dla drugiej i tak dalej.

Podczas przeciągania **dane wejściowe (Resetowanie)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Dane wejściowe (Prześlij)**

![HTMLpageToolbarSubmitButton — zrzut ekranu](../../ide/reference/media/vxsubmit.gif)

Wstawia `input` elementu `type="submit"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Submit1"` jest wstawiany za pierwszy przycisk Prześlij `id="Submit2"` dla drugiej i tak dalej.

Podczas przeciągania **dane wejściowe (Prześlij)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Dane wejściowe (tekst)**

![HTMLpageToolbarTextField — zrzut ekranu](../../ide/reference/media/vxtextfield.gif)

Wstawia `input` elementu `type="text"` w dokumencie. Aby zmienić domyślny tekst, który jest wyświetlany, należy edytować `value` atrybutu. Domyślnie `id="Text1"` jest wstawiany za pierwsze pole tekstowe, `id="Text2"` dla drugiej i tak dalej.

Podczas przeciągania **dane wejściowe (tekst)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Zalecane jest, sprawdź poprawność wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (plik)**

![Strona HTML pola pliku](../../ide/reference/media/vxfilefield.gif)

Wstawia `input` elementu `type="file"` w dokumencie. Domyślnie `id="File1"` jest wstawiany za pierwsze pole pliku `id="File2"` dla drugiej i tak dalej.

Podczas przeciągania **dane wejściowe (plik)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Zalecane jest, sprawdź poprawność wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (hasło)**

![Visual Studio Password Field](../../ide/reference/media/vxpassword.gif)

Wstawia `input` elementu `type="password"`. Domyślnie `id="Password1"` jest wstawiany za pierwsze pole hasło `id="Password2"` dla drugiej i tak dalej.

Podczas przeciągania **dane wejściowe (hasło)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Jeśli Twoja aplikacja przesyła nazwy użytkownika i hasła, należy skonfigurować witryny sieci Web na potrzeby przekazywania szyfrowanie Secure Sockets Layer (SSL). Aby uzyskać więcej informacji, zobacz [Zabezpieczanie połączeń](/previous-versions/tn-archive/bb418917(v=technet.10)). Ponadto zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (pole)**

![HTML strony sieci Web opcja Checkbox w przyborniku](../../ide/reference/media/vxcheckbox.gif)

Wstawia `input` elementu `type="checkbox"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Checkbox1"` jest wstawiany za pierwsze pole wyboru `id="Checkbox2"` dla drugiej i tak dalej.

Podczas przeciągania **dane wejściowe (pole)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Dane wejściowe (przycisk radiowy)**

![VisualStudioHTMLpageRadioButton screenshot](../../ide/reference/media/vxradio.gif)

Wstawia `input` elementu `type="radio"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Radio1"` jest wstawiany za pierwszy przycisk radiowy `id="Radio2"` dla drugiej i tak dalej.

Podczas przeciągania **dane wejściowe (przycisk radiowy)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Dane wejściowe (ukryte)**

![Ukryty element strona HTML](../../ide/reference/media/vxhidden.gif)

Wstawia `input` elementu `type="hidden"`. Domyślnie `id="Hidden1"` jest wstawiany za pierwsze pole ukryte, `id="Hidden2"` dla drugiej i tak dalej.

Podczas przeciągania **dane wejściowe (ukryte)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Obszar tekstu**

![Obszar tekstu w pasku narzędzi strony HTML](../../ide/reference/media/vxtextarea.gif)

Wstawia `textarea` elementu. Możesz zmienić rozmiar obszaru tekstu lub użyj jej pasków przewijania, aby wyświetlić tekst, który wykracza poza jego obszaru wyświetlania. Aby zmienić domyślny tekst, który jest wyświetlany, należy edytować `value` atrybutu. Domyślnie `id="textarea1"` jest wstawiany pierwszego obszaru tekstu `id=" textarea 2"` dla drugiej i tak dalej.

Podczas przeciągania **Textarea** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Zalecane jest, sprawdź poprawność wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Tabela**

![HTMLpageToolbarTable — zrzut ekranu](../../ide/reference/media/vxtable.gif)

Wstawia `table` elementu.

Podczas przeciągania **tabeli** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Obraz**

![Strona HTML elementu obrazu](../../ide/reference/media/vximage.gif)

Wstawia `img` elementu. Edytuj ten element, aby określić jego `src` i jego `alt` tekstu.

Podczas przeciągania **obraz** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<img alt="" src="">
```

**Select**

![Strona HTML listy rozwijanej przybornika](../../ide/reference/media/vxdropdown.gif)

Wstawia listę rozwijaną `select` — element (bez `size` atrybutu). Domyślnie `id="select1"` jest wstawiany za pierwszym polu listy `id="select2"` dla drugiej i tak dalej.

Podczas przeciągania **wybierz** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Można utworzyć wiele wierszy `select` elementu przez zwiększenie wartości właściwości size.

**Linia pozioma**

![Strona HTML poziomy element reguły](../../ide/reference/media/vxhorizontal.gif)

Wstawia `hr` elementu. Aby zwiększyć grubość linii, należy edytować `size` atrybutu.

Podczas przeciągania **linia pozioma** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<hr width="100%" size=1>
```

**Div**

![Strona HTML etykiety](../../ide/reference/media/vxlabel.gif)

Wstawia `div` element, który zawiera `ms_positioning="FlowLayout"` atrybutu. Z wyjątkiem szerokość i wysokość ten element jest taka sama jak Panel układu przepływu. Do formatowania tekstu, który jest zawarty w `div` elementu Dodawanie `class="stylename"` atrybut w tagu otwierającym.

Podczas przeciągania **Div** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Zobacz także

- [Przybornik](../../ide/reference/toolbox.md)
