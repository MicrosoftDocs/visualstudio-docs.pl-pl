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
ms.openlocfilehash: 72492b984e7f47b87ea326fe8ebcce414ee978ec
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926046"
---
# <a name="toolbox-html-tab"></a>Przybornik, karta HTML

Karta **HTML** przybornika zawiera składniki, które są przydatne w przypadku stron sieci Web i formularzy sieci Web. Aby wyświetlić tę kartę, najpierw Otwórz dokument do edycji w projektancie HTML. W menu **Widok** kliknij pozycję **Przybornik**, a następnie kliknij kartę **HTML** w przyborniku.

Aby utworzyć wystąpienie narzędzia na karcie **HTML** , kliknij dwukrotnie narzędzie, aby dodać je do dokumentu w bieżącym punkcie wstawiania, lub wybierz narzędzie i przeciągnij je do żądanej pozycji na powierzchni edycji.

## <a name="ui-elements"></a>Elementy interfejsu użytkownika

Następujące narzędzia są dostępne domyślnie na karcie HTML.

**Pointer**

![ASP.NET Mobile Designer — wskaźnik HTMLpage](../../ide/reference/media/vxpointer.gif)

To narzędzie jest domyślnie zaznaczone, gdy zostanie otwarta jakakolwiek karta przybornika. Nie można go usunąć. Wskaźnik umożliwia przeciąganie obiektów na widok Projekt powierzchni, zmianę ich rozmiaru i zmiana ich położenia na stronie lub w formularzu. Aby uzyskać więcej informacji, zobacz [przybornika](../../ide/reference/toolbox.md).

**Dane wejściowe (przycisk)**

![Przycisk strony sieci Web HTML](../../ide/reference/media/vxbutton.gif)

`input` Wstawia`type="button"`element. Aby zmienić wyświetlany tekst, Edytuj `name` właściwość. Domyślnie, `id="Button1"` jest wstawiany dla pierwszego przycisku, `id="Button2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (przycisk)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Dane wejściowe (Reset)**

![Zrzut ekranu HTMLpageResetButton](../../ide/reference/media/vxreset.gif)

`input` Wstawia`type="reset"`element. Aby zmienić wyświetlany tekst, Edytuj `name` właściwość. Domyślnie, `id="Reset1"` jest wstawiany dla pierwszego `id="Reset2"` przycisku resetowania dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (Reset)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Dane wejściowe (Prześlij)**

![Zrzut ekranu HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif)

`input` Wstawia`type="submit"`element. Aby zmienić wyświetlany tekst, Edytuj `name` właściwość. Domyślnie program `id="Submit1"` jest wstawiany dla pierwszego `id="Submit2"` przycisku przesyłania dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (submit)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Dane wejściowe (tekst)**

![Zrzut ekranu HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif)

`input` Wstawia`type="text"` element do dokumentu. Aby zmienić domyślny tekst, który jest wyświetlany, Edytuj `value` atrybut. Domyślnie, `id="Text1"` jest wstawiany dla pierwszego pola tekstowego, `id="Text2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (tekst)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Zalecane jest zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (plik)**

![Pole pliku strony HTML](../../ide/reference/media/vxfilefield.gif)

`input` Wstawia`type="file"` element do dokumentu. Domyślnie program `id="File1"` jest wstawiany dla pierwszego pola pliku, `id="File2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (pliki)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Zalecane jest zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (hasło)**

![Pole hasła programu Visual Studio](../../ide/reference/media/vxpassword.gif)

`input` Wstawia`type="password"`element. Domyślnie program `id="Password1"` jest wstawiany dla pierwszego pola hasła, `id="Password2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (hasła)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Jeśli aplikacja przesyła nazwy i hasła użytkowników, należy skonfigurować witrynę sieci Web tak, aby używała SSL (SSL) do szyfrowania transmisji. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie połączeń](/previous-versions/tn-archive/bb418917(v=technet.10)). Ponadto zaleca się zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (pole wyboru)**

![Pole wyboru przybornika strony sieci Web HTML](../../ide/reference/media/vxcheckbox.gif)

`input` Wstawia`type="checkbox"`element. Aby zmienić wyświetlany tekst, Edytuj `name` właściwość. Domyślnie, `id="Checkbox1"` jest wstawiany dla pierwszego pola wyboru, `id="Checkbox2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (pola wyboru)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Dane wejściowe (Radio)**

![Zrzut ekranu VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif)

`input` Wstawia`type="radio"`element. Aby zmienić wyświetlany tekst, Edytuj `name` właściwość. Domyślnie, `id="Radio1"` jest wstawiany dla pierwszego przycisku radiowego, `id="Radio2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (Radio)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Dane wejściowe (ukryte)**

![Ukryty element strony HTML](../../ide/reference/media/vxhidden.gif)

`input` Wstawia`type="hidden"`element. Domyślnie, `id="Hidden1"` jest wstawiany dla pierwszego pola ukrytego, `id="Hidden2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (ukryte)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Obszar tekstu**

![Obszar tekstu paska narzędzi HTMLpage](../../ide/reference/media/vxtextarea.gif)

`textarea` Wstawia element. Można zmienić rozmiar obszaru tekstowego lub użyć pasków przewijania do wyświetlania tekstu, który wykracza poza obszar wyświetlania. Aby zmienić domyślny tekst, który jest wyświetlany, Edytuj `value` atrybut. Domyślnie program `id="textarea1"` wstawia pierwszy obszar tekstowy, `id=" textarea 2"` drugi i tak dalej.

Gdy przeciągasz składnik **TextArea** na powierzchnię widok Projekt, do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Zalecane jest zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Tabela**

![Zrzut ekranu HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif)

`table` Wstawia element.

Gdy przeciągniesz **tabelę** na powierzchnię widok Projekt, do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Obraz**

![Element obrazu strony HTML](../../ide/reference/media/vximage.gif)

`img` Wstawia element. Edytuj ten element `alt` , aby określić `src` jego i tekst.

Gdy przeciągasz **obraz** na powierzchnię widok Projekt, do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```html
<img alt="" src="">
```

**Select**

![Lista rozwijana przybornika strony HTML](../../ide/reference/media/vxdropdown.gif)

Wstawia element listy `select` rozwijanej ( `size` bez atrybutu). Domyślnie program `id="select1"` jest wstawiany dla pierwszego pola listy, `id="select2"` dla drugiego i tak dalej.

Po przeciągnięciu **zaznaczenia** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Można utworzyć element wielowierszowy `select` przez zwiększenie wartości właściwości size.

**Linia pozioma**

![Element reguły poziomej strony HTML](../../ide/reference/media/vxhorizontal.gif)

`hr` Wstawia element. Aby zwiększyć grubość linii, Edytuj `size` atrybut.

Po przeciągnięciu **reguły poziomej** na powierzchnię widok projekt do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```html
<hr width="100%" size=1>
```

**Div**

![Etykieta strony HTML](../../ide/reference/media/vxlabel.gif)

Wstawia element, który `ms_positioning="FlowLayout"` zawiera atrybut. `div` Z wyjątkiem szerokości i wysokości ten element jest identyczny z panelem układu przepływu. Aby sformatować tekst zawarty w `div` elemencie, `class="stylename"` Dodaj atrybut do otwierającego znacznika.

Gdy przeciągasz element **DIV** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Zobacz także

- [Przybornik](../../ide/reference/toolbox.md)
