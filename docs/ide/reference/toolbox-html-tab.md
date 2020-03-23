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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0489f534466149a437384d4f21e34f1fa9e98c5b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596440"
---
# <a name="toolbox-html-tab"></a>Przybornik, karta HTML

Karta **HTML** przybornika zawiera składniki przydatne na stronach internetowych i formularzach internetowych. Aby wyświetlić tę kartę, najpierw otwórz dokument do edycji w projektancie HTML. W menu **Widok** kliknij polecenie **Przybornik**, a następnie kliknij kartę **HTML** przybornika.

Aby utworzyć wystąpienie narzędzia na karcie **HTML,** kliknij dwukrotnie narzędzie, aby dodać je do dokumentu w bieżącym punkcie wstawiania, albo zaznacz narzędzie i przeciągnij je w żądane miejsce na powierzchni edycyjnej.

## <a name="ui-elements"></a>Elementy interfejsu użytkownika

Następujące narzędzia są domyślnie dostępne na karcie HTML.

**Wskaźnik**

![ASP.NET Mobile Designer HTMLpage Wskaźnik](../../ide/reference/media/vxpointer.gif)

To narzędzie jest zaznaczone domyślnie po otwarciu dowolnej karty Przybornik. Nie można go usunąć. Wskaźnik umożliwia przeciąganie obiektów na powierzchnię widoku Projekt, ich zmianę rozmiaru i zmianę ich położenia na stronie lub formularzu. Aby uzyskać więcej informacji, zobacz [Przybornik](../../ide/reference/toolbox.md).

**Wejście (przycisk)**

![Przycisk strony internetowej HTML](../../ide/reference/media/vxbutton.gif)

Wstawia `input` element `type="button"`. Aby zmienić wyświetlany tekst, edytuj `name` właściwość. Domyślnie `id="Button1"` jest wstawiany dla `id="Button2"` pierwszego przycisku, dla drugiego i tak dalej.

Podczas przeciągania **wejścia (przycisku)** na powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Wejście (reset)**

![HTMLpageResetButton zrzut ekranu](../../ide/reference/media/vxreset.gif)

Wstawia `input` element `type="reset"`. Aby zmienić wyświetlany tekst, edytuj `name` właściwość. Domyślnie `id="Reset1"` jest wstawiany dla `id="Reset2"` pierwszego przycisku resetowania, dla drugiego i tak dalej.

Podczas przeciągania **wejścia (resetowania)** na powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Dane wejściowe (prześlij)**

![HTMLpageToolbarSubmitButton zrzut ekranu](../../ide/reference/media/vxsubmit.gif)

Wstawia `input` element `type="submit"`. Aby zmienić wyświetlany tekst, edytuj `name` właściwość. Domyślnie `id="Submit1"` jest wstawiany dla `id="Submit2"` pierwszego przycisku przesyłania, dla drugiego i tak dalej.

Podczas przeciągania **danych wejściowych (prześlij)** na powierzchnię widoku Projekt znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Wprowadzanie (tekst)**

![HTMLpageToolbarTextField zrzut ekranu](../../ide/reference/media/vxtextfield.gif)

Wstawia `input` element `type="text"` w dokumencie. Aby zmienić wyświetlany tekst domyślny, `value` edytuj atrybut. Domyślnie `id="Text1"` jest wstawiany dla `id="Text2"` pierwszego pola tekstowego, dla drugiego i tak dalej.

Podczas przeciągania **danych wejściowych (tekst)** na powierzchnię widoku Projekt znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności danych wejściowych użytkownika w witrynach ASP.NET stron sieci Web (Razor).](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Dane wejściowe (plik)**

![Pole pliku strony HTML](../../ide/reference/media/vxfilefield.gif)

Wstawia `input` element `type="file"` w dokumencie. Domyślnie `id="File1"` jest wstawiany dla `id="File2"` pierwszego pola pliku, dla drugiego i tak dalej.

Podczas przeciągania **input (File)** na powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności danych wejściowych użytkownika w witrynach ASP.NET stron sieci Web (Razor).](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Dane wejściowe (hasło)**

![Pole hasła programu Visual Studio](../../ide/reference/media/vxpassword.gif)

Wstawia `input` element `type="password"`. Domyślnie `id="Password1"` jest wstawiany dla `id="Password2"` pierwszego pola hasła, dla drugiego i tak dalej.

Podczas przeciągania **danych wejściowych (hasło)** na powierzchnię widoku Projekt do dokumentu wstawiano znaczniki HTML, takie jak następujące:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Jeśli aplikacja przesyła nazwy użytkowników i hasła, należy skonfigurować witrynę sieci Web tak, aby do szyfrowania transmisji używała warstwy Secure Sockets Layer (SSL). Aby uzyskać więcej informacji, zobacz [Zabezpieczanie połączeń](/previous-versions/tn-archive/bb418917(v=technet.10)). Ponadto zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności danych wejściowych użytkownika w witrynach ASP.NET stron sieci Web (Razor).](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Wprowadzanie (pole wyboru)**

![Opcja pola wyboru pola wyboru pola narzędziowego strony HTML](../../ide/reference/media/vxcheckbox.gif)

Wstawia `input` element `type="checkbox"`. Aby zmienić wyświetlany tekst, edytuj `name` właściwość. Domyślnie `id="Checkbox1"` jest wstawiany dla `id="Checkbox2"` pierwszego pola wyboru, dla drugiego i tak dalej.

Podczas przeciągania **opcji Input (pole wyboru)** na powierzchnię widoku Projekt do dokumentu wstawiano znaczniki HTML, takie jak następujące:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Wejście (radio)**

![VisualStudioHTMLpageRadioButton zrzut ekranu](../../ide/reference/media/vxradio.gif)

Wstawia `input` element `type="radio"`. Aby zmienić wyświetlany tekst, edytuj `name` właściwość. Domyślnie `id="Radio1"` jest wstawiany dla `id="Radio2"` pierwszego przycisku radiowego, dla drugiego i tak dalej.

Podczas przeciągania **wejścia (radia)** na powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Wejście (ukryte)**

![Ukryty element strony HTML](../../ide/reference/media/vxhidden.gif)

Wstawia `input` element `type="hidden"`. Domyślnie `id="Hidden1"` jest wstawiany dla `id="Hidden2"` pierwszego ukrytego pola, dla drugiego i tak dalej.

Podczas przeciągania **input (Hidden)** na powierzchnię widoku Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Obszar tekstu**

![Obszar tekstowy paska narzędzi HTMLpage](../../ide/reference/media/vxtextarea.gif)

Wstawia `textarea` element. Można zmienić rozmiar obszaru tekstu lub użyć jego pasków przewijania, aby wyświetlić tekst wykraczający poza obszar wyświetlania. Aby zmienić wyświetlany tekst domyślny, `value` edytuj atrybut. Domyślnie `id="textarea1"` jest wstawiany pierwszy `id=" textarea 2"` obszar tekstu, dla drugiego i tak dalej.

Podczas przeciągania **obszaru tekstowego** na powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności danych wejściowych użytkownika w witrynach ASP.NET stron sieci Web (Razor).](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Tabeli**

![HTMLpageToolbarTable zrzut ekranu](../../ide/reference/media/vxtable.gif)

Wstawia `table` element.

Podczas przeciągania **tabeli** na powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Obrazu**

![Element obrazu strony HTML](../../ide/reference/media/vximage.gif)

Wstawia `img` element. Edytuj ten element, `src` aby `alt` określić jego i jego tekst.

Podczas przeciągania **obrazu** na powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<img alt="" src="">
```

**Wybierz**

![Strona HTML Przybornik narzędzi rozwijany](../../ide/reference/media/vxdropdown.gif)

Wstawia element `select` rozwijany `size` (bez atrybutu). Domyślnie `id="select1"` jest wstawiany dla `id="select2"` pierwszego pola listy, dla drugiego i tak dalej.

Po przeciągnięciu **opcji Zaznacz na** powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Można utworzyć element wielowierszowy, `select` zwiększając wartość właściwości size.

**Reguła horyzontalna**

![Element reguły poziomej strony HTML](../../ide/reference/media/vxhorizontal.gif)

Wstawia `hr` element. Aby zwiększyć grubość linii, `size` edytuj atrybut.

Podczas przeciągania **reguły poziomej** na powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<hr width="100%" size=1>
```

**Div**

![Etykieta strony HTML](../../ide/reference/media/vxlabel.gif)

Wstawia `div` element, `ms_positioning="FlowLayout"` który zawiera atrybut. Z wyjątkiem szerokości i wysokości, ten element jest identyczny z Panelem układu przepływu. Aby sformatować tekst zawarty `div` w elemencie, dodaj `class="stylename"` atrybut do znacznika otwierającego.

Podczas przeciągania **wskaźnika Div** na powierzchnię widoku Projekt do dokumentu wstawiany jest znacznik HTML, taki jak następujący:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Zobacz też

- [Przybornik](../../ide/reference/toolbox.md)
