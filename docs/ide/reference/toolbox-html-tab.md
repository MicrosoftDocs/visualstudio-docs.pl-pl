---
title: Przybornik, karta HTML
description: Więcej informacji na temat składników HTML znajdziesz na karcie HTML okna przybornika.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f91e832e33d6a65d9fc70ee594d0c0670242306e
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560463"
---
# <a name="toolbox-html-tab"></a>Przybornik, karta HTML

Karta **HTML** przybornika zawiera składniki, które są przydatne w przypadku stron sieci Web i formularzy sieci Web. Aby wyświetlić tę kartę, najpierw Otwórz dokument do edycji w projektancie HTML. W menu **Widok** kliknij pozycję **Przybornik**, a następnie kliknij kartę **HTML** w przyborniku.

Aby utworzyć wystąpienie narzędzia na karcie **HTML** , kliknij dwukrotnie narzędzie, aby dodać je do dokumentu w bieżącym punkcie wstawiania, lub wybierz narzędzie i przeciągnij je do żądanej pozycji na powierzchni edycji.

## <a name="ui-elements"></a>Elementy interfejsu użytkownika

Następujące narzędzia są dostępne domyślnie na karcie HTML.

**Przytrzymaj**

![ASP.NET Mobile Designer — wskaźnik HTMLpage](../../ide/reference/media/vxpointer.gif)

To narzędzie jest domyślnie zaznaczone, gdy zostanie otwarta jakakolwiek karta przybornika. Nie można go usunąć. Wskaźnik umożliwia przeciąganie obiektów na widok Projekt powierzchni, zmianę ich rozmiaru i zmiana ich położenia na stronie lub w formularzu. Aby uzyskać więcej informacji, zobacz [Przybornik](../../ide/reference/toolbox.md).

**Dane wejściowe (przycisk)**

![Przycisk strony sieci Web HTML](../../ide/reference/media/vxbutton.gif)

Wstawia `input` element `type="button"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie, `id="Button1"` jest wstawiany dla pierwszego przycisku, `id="Button2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (przycisk)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Dane wejściowe (Reset)**

![Zrzut ekranu HTMLpageResetButton](../../ide/reference/media/vxreset.gif)

Wstawia `input` element `type="reset"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie, `id="Reset1"` jest wstawiany dla pierwszego przycisku resetowania `id="Reset2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (Reset)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Dane wejściowe (Prześlij)**

![Zrzut ekranu HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif)

Wstawia `input` element `type="submit"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie program `id="Submit1"` jest wstawiany dla pierwszego przycisku przesyłania `id="Submit2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (submit)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Dane wejściowe (tekst)**

![Zrzut ekranu HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif)

Wstawia `input` element `type="text"` do dokumentu. Aby zmienić domyślny tekst, który jest wyświetlany, Edytuj `value` atrybut. Domyślnie, `id="Text1"` jest wstawiany dla pierwszego pola tekstowego, `id="Text2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (tekst)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Zalecane jest zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (plik)**

![Pole pliku strony HTML](../../ide/reference/media/vxfilefield.gif)

Wstawia `input` element `type="file"` do dokumentu. Domyślnie program `id="File1"` jest wstawiany dla pierwszego pola pliku, `id="File2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (pliki)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Zalecane jest zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (hasło)**

![Pole hasła programu Visual Studio](../../ide/reference/media/vxpassword.gif)

Wstawia `input` element `type="password"` . Domyślnie program `id="Password1"` jest wstawiany dla pierwszego pola hasła, `id="Password2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (hasła)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Jeśli aplikacja przesyła nazwy i hasła użytkowników, należy skonfigurować witrynę sieci Web tak, aby używała SSL (SSL) do szyfrowania transmisji. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie połączeń](/previous-versions/tn-archive/bb418917(v=technet.10)). Ponadto zaleca się zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (pole wyboru)**

![Pole wyboru przybornika strony sieci Web HTML](../../ide/reference/media/vxcheckbox.gif)

Wstawia `input` element `type="checkbox"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie, `id="Checkbox1"` jest wstawiany dla pierwszego pola wyboru, `id="Checkbox2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (pola wyboru)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Dane wejściowe (Radio)**

![Zrzut ekranu VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif)

Wstawia `input` element `type="radio"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie, `id="Radio1"` jest wstawiany dla pierwszego przycisku radiowego, `id="Radio2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (Radio)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Dane wejściowe (ukryte)**

![Ukryty element strony HTML](../../ide/reference/media/vxhidden.gif)

Wstawia `input` element `type="hidden"` . Domyślnie, `id="Hidden1"` jest wstawiany dla pierwszego pola ukrytego, `id="Hidden2"` dla drugiego i tak dalej.

Gdy przeciągasz **dane wejściowe (ukryte)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Obszar tekstu**

![Obszar tekstu paska narzędzi HTMLpage](../../ide/reference/media/vxtextarea.gif)

Wstawia `textarea` element. Można zmienić rozmiar obszaru tekstowego lub użyć pasków przewijania do wyświetlania tekstu, który wykracza poza obszar wyświetlania. Aby zmienić domyślny tekst, który jest wyświetlany, Edytuj `value` atrybut. Domyślnie program `id="textarea1"` wstawia pierwszy obszar tekstowy, `id=" textarea 2"` drugi i tak dalej.

Gdy przeciągasz składnik **TextArea** na powierzchnię widok Projekt, do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Zalecane jest zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika w witrynach ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Tabela**

![Zrzut ekranu HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif)

Wstawia `table` element.

Gdy przeciągniesz **tabelę** na powierzchnię widok Projekt, do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Obraz**

![Element obrazu strony HTML](../../ide/reference/media/vximage.gif)

Wstawia `img` element. Edytuj ten element, aby określić jego `src` i `alt` tekst.

Gdy przeciągasz **obraz** na powierzchnię widok Projekt, do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```html
<img alt="" src="">
```

**Wybierz**

![Lista rozwijana przybornika strony HTML](../../ide/reference/media/vxdropdown.gif)

Wstawia element listy rozwijanej `select` (bez `size` atrybutu). Domyślnie program `id="select1"` jest wstawiany dla pierwszego pola listy, `id="select2"` dla drugiego i tak dalej.

Po przeciągnięciu **zaznaczenia** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Można utworzyć element wielowierszowy `select` przez zwiększenie wartości właściwości size.

**Linia pozioma**

![Element reguły poziomej strony HTML](../../ide/reference/media/vxhorizontal.gif)

Wstawia `hr` element. Aby zwiększyć grubość linii, Edytuj `size` atrybut.

Po przeciągnięciu **reguły poziomej** na powierzchnię widok projekt do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```html
<hr width="100%" size=1>
```

**Służąc**

![Etykieta strony HTML](../../ide/reference/media/vxlabel.gif)

Wstawia `div` element, który zawiera `ms_positioning="FlowLayout"` atrybut. Z wyjątkiem szerokości i wysokości ten element jest identyczny z panelem układu przepływu. Aby sformatować tekst zawarty w `div` elemencie, Dodaj `class="stylename"` atrybut do otwierającego znacznika.

Gdy przeciągasz element **DIV** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Zobacz także

- [Przybornik](../../ide/reference/toolbox.md)
