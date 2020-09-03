---
title: Przybornik, karta HTML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4474f2a0823b5599da30706daedff6e5cd1fc0f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851659"
---
# <a name="toolbox-html-tab"></a>Przybornik, karta HTML
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Karta **HTML** przybornika zawiera składniki, które są przydatne w przypadku stron sieci Web i formularzy sieci Web. Aby wyświetlić tę kartę, najpierw Otwórz dokument do edycji w projektancie HTML. W menu **Widok** kliknij pozycję **Przybornik**, a następnie kliknij kartę **HTML** w przyborniku.

 Aby utworzyć wystąpienie narzędzia na karcie **HTML** , kliknij dwukrotnie narzędzie, aby dodać je do dokumentu w bieżącym punkcie wstawiania, lub wybierz narzędzie i przeciągnij je do żądanej pozycji na powierzchni edycji.

## <a name="tasks"></a>Zadania

- [Instrukcje: Zarządzanie oknem przybornika](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)

- [Instrukcje: manipulowanie kartami przybornika](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)

## <a name="ui-elements"></a>Elementy interfejsu użytkownika
 Następujące narzędzia są dostępne domyślnie na karcie HTML.

 **Wskaźnik** ![HTMLpage projektanta ASP.net Mobile Designer](../../ide/reference/media/vxpointer.gif "vxPointer")

 To narzędzie jest domyślnie zaznaczone, gdy zostanie otwarta jakakolwiek karta przybornika. Nie można go usunąć. Wskaźnik umożliwia przeciąganie obiektów na widok Projekt powierzchni, zmianę ich rozmiaru i zmiana ich położenia na stronie lub w formularzu. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie oknem przybornika](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) i [instrukcje: manipulowanie kartami przybornika](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 **Input (Button)** ![Przycisk strony sieci Web w formacie HTML](../../ide/reference/media/vxbutton.gif "vxButton")

 Wstawia `input` element `type="button"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie, `id="Button1"` jest wstawiany dla pierwszego przycisku, `id="Button2"` dla drugiego i tak dalej.

 Gdy przeciągasz **dane wejściowe (przycisk)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<input id="Button1" type="button" value="Button" name="Button1">
```

 Aby uzyskać więcej informacji, zobacz [kontrolki danych wejściowych HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputButton Server Control — składnia deklaracyjne](https://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: How to: Create scripts and Edit obsługi zdarzeń](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Button Web Server Controls map zawartości](https://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf),, <xref:System.Web.UI.HtmlControls.HtmlInputButton> <xref:System.Web.UI.HtmlControls.HtmlButton> i <xref:System.Web.UI.WebControls.Button> .

 **Wejście (Reset)** — ![zrzut ekranu HTMLpageResetButton](../../ide/reference/media/vxreset.gif "vxReset")

 Wstawia `input` element `type="reset"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie, `id="Reset1"` jest wstawiany dla pierwszego przycisku resetowania `id="Reset2"` dla drugiego i tak dalej.

 Gdy przeciągasz **dane wejściowe (Reset)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

 Aby uzyskać więcej informacji, zobacz [kontrolki danych wejściowych HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składnia deklaratywna HtmlInputReset Server Control](https://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> i <xref:System.Web.UI.WebControls.Button> .

 ![Zrzut ekranu](../../ide/reference/media/vxsubmit.gif "vxSubmit") **danych wejściowych (submit)** HTMLpageToolbarSubmitButton

 Wstawia `input` element `type="submit"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie program `id="Submit1"` jest wstawiany dla pierwszego przycisku przesyłania `id="Submit2"` dla drugiego i tak dalej.

 Gdy przeciągasz **dane wejściowe (submit)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

 Aby uzyskać więcej informacji, zobacz [kontrolki danych wejściowych HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składnia deklaratywna HtmlInputSubmit Server Control](https://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> i <xref:System.Web.UI.WebControls.Button> .

 ![Zrzut ekranu](../../ide/reference/media/vxtextfield.gif "vxTextfield") **danych wejściowych (tekstowych)** HTMLpageToolbarTextField

 Wstawia `input` element `type="text"` do dokumentu. Aby zmienić domyślny tekst, który jest wyświetlany, Edytuj `value` atrybut. Domyślnie, `id="Text1"` jest wstawiany dla pierwszego pola tekstowego, `id="Text2"` dla drugiego i tak dalej.

 Gdy przeciągasz **dane wejściowe (tekst)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

 Aby uzyskać więcej informacji, zobacz kontrolki [danych wejściowych HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputText Server Control — składnia deklaratywna](https://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [Omówienie kontrolki serwera sieci Web](https://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText> i <xref:System.Web.UI.WebControls.TextBox> .

> [!IMPORTANT]
> Zalecane jest zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika na stronach sieci Web ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 Pole **wejściowe (plik)** ![HTML pliku strony](../../ide/reference/media/vxfilefield.gif "vxFilefield")

 Wstawia `input` element `type="file"` do dokumentu. Domyślnie program `id="File1"` jest wstawiany dla pierwszego pola pliku, `id="File2"` dla drugiego i tak dalej.

 Gdy przeciągasz **dane wejściowe (pliki)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<input id="File1" type="file" name="File1">
```

 Aby uzyskać więcej informacji, zobacz [kontrolki danych wejściowych HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składnia deklaratywna HtmlInputFile Server Control](https://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6)i <xref:System.Web.UI.HtmlControls.HtmlInputFile> .

> [!IMPORTANT]
> Zalecane jest zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika na stronach sieci Web ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 Pole hasła dla **danych wejściowych (hasła)** ![programu Visual Studio](../../ide/reference/media/vxpassword.gif "vxPassword")

 Wstawia `input` element `type="password"` . Domyślnie program `id="Password1"` jest wstawiany dla pierwszego pola hasła, `id="Password2"` dla drugiego i tak dalej.

 Gdy przeciągasz **dane wejściowe (hasła)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<input id="Password1" type="password" name="Password1">
```

 Aby uzyskać więcej informacji, zobacz kontrolki [danych wejściowych HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputPassword Server Control — składnia deklaratywna](https://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [instrukcje: Ustawianie kontrolki serwera sieci Web dla wpisu hasła](https://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310)oraz [Przewodnik: sprawdzanie poprawności danych wejściowych użytkownika na stronie formularzy sieci Web](https://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).

> [!IMPORTANT]
> Jeśli aplikacja przesyła nazwy i hasła użytkowników, należy skonfigurować witrynę sieci Web tak, aby używała SSL (SSL) do szyfrowania transmisji. Aby uzyskać więcej informacji, zobacz "Zabezpieczanie połączeń przy użyciu protokołu SSL" w [Przewodniku obsługi usług IIS](https://technet.microsoft.com/library/cc732976(v=WS.10).aspx). Ponadto zaleca się zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika na stronach sieci Web ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Wejściowy (pole wyboru)** pole ![wyboru przybornika strony HTML](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")

 Wstawia `input` element `type="checkbox"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie, `id="Checkbox1"` jest wstawiany dla pierwszego pola wyboru, `id="Checkbox2"` dla drugiego i tak dalej.

 Gdy przeciągasz **dane wejściowe (pola wyboru)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

 Aby uzyskać więcej informacji, zobacz kontrolki [danych wejściowych HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputCheckBox Server — składnia deklaracyjne](https://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [CheckBox i formant CheckBoxList serwera sieci Web — Omówienie](https://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> i <xref:System.Web.UI.WebControls.CheckBox> .

 ![Zrzut ekranu](../../ide/reference/media/vxradio.gif "vxRadio") **danych wejściowych (Radio)** VisualStudioHTMLpageRadioButton

 Wstawia `input` element `type="radio"` . Aby zmienić wyświetlany tekst, Edytuj `name` Właściwość. Domyślnie, `id="Radio1"` jest wstawiany dla pierwszego przycisku radiowego, `id="Radio2"` dla drugiego i tak dalej.

 Gdy przeciągasz **dane wejściowe (Radio)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<input id="Radio1" type="radio" name="Radio1">
```

 Aby uzyskać więcej informacji, zobacz kontrolki [danych wejściowych HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputRadioButton Server — Składnia deklaratywna](https://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), element [RadioButton oraz formanty serwera sieci Web RadioButtonList](https://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> i <xref:System.Web.UI.WebControls.RadioButton> .

 Tekst **wejściowy (ukryty)** ![ukryty element strony HTML](../../ide/reference/media/vxhidden.gif "vxhidden")

 Wstawia `input` element `type="hidden"` . Domyślnie, `id="Hidden1"` jest wstawiany dla pierwszego pola ukrytego, `id="Hidden2"` dla drugiego i tak dalej.

 Gdy przeciągasz **dane wejściowe (ukryte)** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<input id="Hidden1" type="hidden" name="Hidden1">
```

 Aby uzyskać więcej informacji, zobacz [kontrolki danych wejściowych HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składnia deklaratywna HtmlInputHidden Server Control](https://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9)i <xref:System.Web.UI.HtmlControls.HtmlInputHidden> .

 **Textarea** ![Obszar tekstu paska narzędzi HTMLpage](../../ide/reference/media/vxtextarea.gif "vxTextarea") TextArea

 Wstawia `textarea` element. Można zmienić rozmiar obszaru tekstowego lub użyć pasków przewijania do wyświetlania tekstu, który wykracza poza obszar wyświetlania. Aby zmienić domyślny tekst, który jest wyświetlany, Edytuj `value` atrybut. Domyślnie program `id="textarea1"` wstawia pierwszy obszar tekstowy, `id=" textarea 2"` drugi i tak dalej.

 Gdy przeciągasz składnik **TextArea** na powierzchnię widok Projekt, do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

 Aby uzyskać więcej informacji, zobacz [HtmlTextArea Server Control — składnia deklaracyjne](https://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea> i <xref:System.Web.UI.WebControls.TextBox> .

> [!IMPORTANT]
> Zalecane jest zweryfikowanie wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych wejściowych użytkownika na stronach sieci Web ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Table** ![Zrzut ekranu HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "vxTable") tabeli

 Wstawia `table` element.

 Gdy przeciągniesz **tabelę** na powierzchnię widok Projekt, do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

 Aby uzyskać więcej informacji, zobacz temat składnia, [tabela, TableRow i formant serwera sieci Web](https://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a)w [formacie HTML](https://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9). <xref:System.Web.UI.HtmlControls.HtmlTable> <xref:System.Web.UI.WebControls.Table>

 **Image** ![Element obrazu strony HTML](../../ide/reference/media/vximage.gif "vxImage") obrazu

 Wstawia `img` element. Edytuj ten element, aby określić jego `src` i `alt` tekst.

 Gdy przeciągasz **obraz** na powierzchnię widok Projekt, do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```
<img alt="" src="">
```

 Aby uzyskać więcej informacji, zobacz [składnia deklaracyjnego sterowania serwerem HtmlImage](https://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [Omówienie kontrolki serwer sieci Web obrazu](https://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9),, <xref:System.Web.UI.HtmlControls.HtmlImage> <xref:System.Web.UI.HtmlControls.HtmlInputImage> , i <xref:System.Web.UI.WebControls.Image> .

 **Wybierz** ![listę rozwijaną przybornika strony HTML](../../ide/reference/media/vxdropdown.gif "vxDropdown")

 Wstawia element listy rozwijanej `select` (bez `size` atrybutu). Domyślnie program `id="select1"` jest wstawiany dla pierwszego pola listy, `id="select2"` dla drugiego i tak dalej.

 Po przeciągnięciu **zaznaczenia** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<select id="select1" name="select1"><option selected></option></select>
```

 Można utworzyć element wielowierszowy `select` przez zwiększenie wartości właściwości size.

 Aby uzyskać więcej informacji, zobacz [HtmlSelect Server Control — składnia deklaratywna](https://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: How to: Create scripts and Edit procedurs](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d)Controls, [reDropDownListing serwer sieci Web](https://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [Omówienie kontrolki serwer sieci Web](https://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97) <xref:System.Web.UI.HtmlControls.HtmlSelect> <xref:System.Web.UI.WebControls.DropDownList>

 **Linia pozioma** ![strona HTML dla reguły poziomej](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")

 Wstawia `hr` element. Aby zwiększyć grubość linii, Edytuj `size` atrybut.

 Po przeciągnięciu **reguły poziomej** na powierzchnię widok projekt do dokumentu zostanie wstawiony znacznik HTML podobny do następującego:

```
<hr width="100%" size=1>
```

 Aby uzyskać więcej informacji, zobacz [kontrolka reguł HTML w poziomie](https://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).

 **Div** ![Etykieta strony HTML](../../ide/reference/media/vxlabel.gif "vxLabel") DIV

 Wstawia `div` element, który zawiera `ms_positioning="FlowLayout"` atrybut. Z wyjątkiem szerokości i wysokości ten element jest identyczny z panelem układu przepływu. Aby sformatować tekst zawarty w `div` elemencie, Dodaj `class="stylename"` atrybut do otwierającego znacznika.

 Gdy przeciągasz element **DIV** na powierzchnię widok Projekt, znaczniki HTML, takie jak następujące, są wstawiane do dokumentu:

```
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

 Aby uzyskać więcej informacji, zobacz [kontrolka HTML DIV](https://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Opis kontrolki serwera sieci Web](https://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac)i <xref:System.Web.UI.WebControls.Label> .

## <a name="see-also"></a>Zobacz też
 [Przybornik](../../ide/reference/toolbox.md) [— karta standardowa,](https://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870) [kontrolki HTML](https://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be) przybornika
