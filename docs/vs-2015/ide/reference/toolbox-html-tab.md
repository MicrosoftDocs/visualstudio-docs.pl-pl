---
title: Toolbox, HTML Tab | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6c0603bd820990789af0d9bbca147acd7004e1a1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097534"
---
# <a name="toolbox-html-tab"></a>Przybornik, karta HTML
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**HTML** karta w przyborniku zawiera składniki, które przydają się na stronach sieci Web i formularzy sieci Web. Aby wyświetlić tę kartę, należy najpierw otworzyć dokument do edycji w Projektancie HTML. Na **widoku** menu, kliknij przycisk **przybornika**, a następnie kliknij przycisk **HTML** kartę przybornika.  
  
 Aby utworzyć wystąpienie narzędzia na **HTML** kartę, albo kliknij dwukrotnie narzędzie, aby dodać go do dokumentu w bieżącym punkcie wstawiania lub wybierz narzędzie i przeciągnij go do żądanej pozycji na powierzchni edycji.  
  
## <a name="tasks"></a>Zadania  
  
- [Instrukcje: Zarządzanie oknem przybornika](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
- [Instrukcje: Manipulowanie karty przybornika](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## <a name="ui-elements"></a>Elementy interfejsu użytkownika  
 Następujące narzędzia są dostępne na karcie HTML domyślnie.  
  
 **Pointer**  
 ![ASP.NET Mobile projektanta HTMLpage wskaźnik](../../ide/reference/media/vxpointer.gif "vxPointer")  
  
 To narzędzie jest domyślnie zaznaczona, po otwarciu dowolnej karcie przybornika. Nie można usunąć. Wskaźnik umożliwia przeciągnij obiekty na powierzchni projektowej widoku, zmieniać ich rozmiar i zmiany ich położenia na stronie lub formularza. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie oknem przybornika](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) i [jak: Karty przybornika manipulowania](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Dane wejściowe (przycisk)**  
 ![Przycisk strony internetowej HTML](../../ide/reference/media/vxbutton.gif "vxButton")  
  
 Wstawia `input` elementu `type="button"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Button1"` jest wstawiany za pierwszy przycisk `id="Button2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **dane wejściowe (przycisk)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Aby uzyskać więcej informacji, zobacz [kontrolki wprowadzania HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składni deklaratywnej kontroli serwera HtmlInputButton](http://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: Instrukcje: Tworzenie skryptów i edytowanie programów obsługi zdarzeń](http://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [serwera sieci Web przycisku kontrolki zawartości mapy](http://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton>, i <xref:System.Web.UI.WebControls.Button>.  
  
 **Dane wejściowe (Resetowanie)**  
 ![HTMLpageResetButton — zrzut ekranu](../../ide/reference/media/vxreset.gif "vxReset")  
  
 Wstawia `input` elementu `type="reset"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Reset1"` dodaje się do pierwszego przycisku, resetowania `id="Reset2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **dane wejściowe (Resetowanie)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Aby uzyskać więcej informacji, zobacz [kontrolki wprowadzania HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składni deklaratywnej kontroli serwera HtmlInputReset](http://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, i <xref:System.Web.UI.WebControls.Button>.  
  
 **Dane wejściowe (Prześlij)**  
 ![HTMLpageToolbarSubmitButton — zrzut ekranu](../../ide/reference/media/vxsubmit.gif "vxSubmit")  
  
 Wstawia `input` elementu `type="submit"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Submit1"` jest wstawiany za pierwszy przycisk Prześlij `id="Submit2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **dane wejściowe (Prześlij)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Aby uzyskać więcej informacji, zobacz [kontrolki wprowadzania HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składni deklaratywnej kontroli serwera HtmlInputSubmit](http://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, i <xref:System.Web.UI.WebControls.Button>.  
  
 **Dane wejściowe (tekst)**  
 ![HTMLpageToolbarTextField — zrzut ekranu](../../ide/reference/media/vxtextfield.gif "vxTextfield")  
  
 Wstawia `input` elementu `type="text"` w dokumencie. Aby zmienić domyślny tekst, który jest wyświetlany, należy edytować `value` atrybutu. Domyślnie `id="Text1"` jest wstawiany za pierwsze pole tekstowe, `id="Text2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **dane wejściowe (tekst)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Aby uzyskać więcej informacji, zobacz [kontrolki wprowadzania HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składni deklaratywnej kontroli serwera HtmlInputText](http://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [omówienie kontrolki serwera sieci Web w polu tekstowym](http://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText>, i <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Zalecane jest, sprawdź poprawność wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w produkcie ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Dane wejściowe (plik)**  
 ![Strona HTML pola pliku](../../ide/reference/media/vxfilefield.gif "vxFilefield")  
  
 Wstawia `input` elementu `type="file"` w dokumencie. Domyślnie `id="File1"` jest wstawiany za pierwsze pole pliku `id="File2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **dane wejściowe (plik)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Aby uzyskać więcej informacji, zobacz [kontrolki wprowadzania HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składni deklaratywnej kontroli serwera HtmlInputFile](http://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6), i <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
>  Zalecane jest, sprawdź poprawność wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w produkcie ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Dane wejściowe (hasło)**  
 ![Visual Studio Password Field](../../ide/reference/media/vxpassword.gif "vxPassword")  
  
 Wstawia `input` elementu `type="password"`. Domyślnie `id="Password1"` jest wstawiany za pierwsze pole hasło `id="Password2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **dane wejściowe (hasło)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Aby uzyskać więcej informacji, zobacz [kontrolki wprowadzania HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składni deklaratywnej kontroli serwera HtmlInputPassword](http://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [jak: Ustaw formant serwera sieci Web pole tekstowe do wprowadzenia hasła](http://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310), i [instruktażu: Walidacja danych wejściowych użytkownika w sieci Web Forms strony](http://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).  
  
> [!IMPORTANT]
>  Jeśli Twoja aplikacja przesyła nazwy użytkownika i hasła, należy skonfigurować witryny sieci Web na potrzeby przekazywania szyfrowanie Secure Sockets Layer (SSL). Aby uzyskać więcej informacji, zobacz "Zabezpieczenia połączeń z protokołem SSL" w [przewodniku obsługi usług IIS](http://go.microsoft.com/fwlink/?linkid=47856). Ponadto zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w produkcie ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Dane wejściowe (pole)**  
 ![HTML strony sieci Web opcja Checkbox w przyborniku](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  
  
 Wstawia `input` elementu `type="checkbox"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Checkbox1"` jest wstawiany za pierwsze pole wyboru `id="Checkbox2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **dane wejściowe (pole)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Aby uzyskać więcej informacji, zobacz [kontrolki wprowadzania HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składni deklaratywnej kontroli serwera HtmlInputCheckBox](http://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [pole wyboru i omówienie kontrolki serwera sieci Web CheckBoxList](http://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox>, i <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Dane wejściowe (przycisk radiowy)**  
 ![VisualStudioHTMLpageRadioButton screenshot](../../ide/reference/media/vxradio.gif "vxRadio")  
  
 Wstawia `input` elementu `type="radio"`. Aby zmienić tekst, który jest wyświetlany, należy edytować `name` właściwości. Domyślnie `id="Radio1"` jest wstawiany za pierwszy przycisk radiowy `id="Radio2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **dane wejściowe (przycisk radiowy)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Aby uzyskać więcej informacji, zobacz [kontrolki wprowadzania HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składni deklaratywnej kontroli serwera HtmlInputRadioButton](http://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton i omówienie kontrolki serwera sieci Web RadioButtonList](http://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton>, i <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Dane wejściowe (ukryte)**  
 ![Strona HTML — ukryty element](../../ide/reference/media/vxhidden.gif "vxhidden")  
  
 Wstawia `input` elementu `type="hidden"`. Domyślnie `id="Hidden1"` jest wstawiany za pierwsze pole ukryte, `id="Hidden2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **dane wejściowe (ukryte)** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Aby uzyskać więcej informacji, zobacz [kontrolki wprowadzania HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [składni deklaratywnej kontroli serwera HtmlInputHidden](http://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9), i <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **Obszar tekstu**  
 ![Obszar tekstu na pasku narzędzi strony HTML](../../ide/reference/media/vxtextarea.gif "vxTextarea")  
  
 Wstawia `textarea` elementu. Możesz zmienić rozmiar obszaru tekstu lub użyj jej pasków przewijania, aby wyświetlić tekst, który wykracza poza jego obszaru wyświetlania. Aby zmienić domyślny tekst, który jest wyświetlany, należy edytować `value` atrybutu. Domyślnie `id="textarea1"` jest wstawiany pierwszego obszaru tekstu `id=" textarea 2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **Textarea** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Aby uzyskać więcej informacji, zobacz [składni deklaratywnej kontroli serwera HtmlTextArea](http://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea>, i <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Zalecane jest, sprawdź poprawność wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w produkcie ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Tabela**  
 ![HTMLpageToolbarTable — zrzut ekranu](../../ide/reference/media/vxtable.gif "vxTable")  
  
 Wstawia `table` elementu.  
  
 Podczas przeciągania **tabeli** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Aby uzyskać więcej informacji, zobacz [składni deklaratywnej kontroli serwera HtmlTable](http://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [tabeli wymagają elementu oraz omówienie kontrolki serwera sieci Web TableCell](http://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable>, i <xref:System.Web.UI.WebControls.Table>.  
  
 **Obraz**  
 ![Strona HTML elementu obrazu](../../ide/reference/media/vximage.gif "vxImage")  
  
 Wstawia `img` elementu. Edytuj ten element, aby określić jego `src` i jego `alt` tekstu.  
  
 Podczas przeciągania **obraz** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<img alt="" src="">  
```  
  
 Aby uzyskać więcej informacji, zobacz [składni deklaratywnej kontroli serwera HtmlImage](http://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [omówienie kontrolki serwera sieci Web obraz](http://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage>, i <xref:System.Web.UI.WebControls.Image>.  
  
 **Select**  
 ![Strona HTML listy rozwijanej przybornika](../../ide/reference/media/vxdropdown.gif "vxDropdown")  
  
 Wstawia listę rozwijaną `select` — element (bez `size` atrybutu). Domyślnie `id="select1"` jest wstawiany za pierwszym polu listy `id="select2"` dla drugiej i tak dalej.  
  
 Podczas przeciągania **wybierz** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 Można utworzyć wiele wierszy `select` elementu przez zwiększenie wartości właściwości size.  
  
 Aby uzyskać więcej informacji, zobacz [składni deklaratywnej kontroli serwera HtmlSelect](http://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: Instrukcje: Tworzenie skryptów i edytowanie programów obsługi zdarzeń](http://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [omówienie kontrolki serwera sieci Web DropDownList](http://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [omówienie kontrolki serwera sieci Web ListBox](http://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect>, i <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Linia pozioma**  
 ![Strona HTML poziomy elementu reguły](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  
  
 Wstawia `hr` elementu. Aby zwiększyć grubość linii, należy edytować `size` atrybutu.  
  
 Podczas przeciągania **linia pozioma** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<hr width="100%" size=1>   
```  
  
 Aby uzyskać więcej informacji, zobacz [poziomy reguły combo](http://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).  
  
 **Div**  
 ![Strona HTML etykiety](../../ide/reference/media/vxlabel.gif "vxLabel")  
  
 Wstawia `div` element, który zawiera `ms_positioning="FlowLayout"` atrybutu. Z wyjątkiem szerokość i wysokość ten element jest taka sama jak Panel układu przepływu. Do formatowania tekstu, który jest zawarty w `div` elementu Dodawanie `class="stylename"` atrybut w tagu otwierającym.  
  
 Podczas przeciągania **Div** wstawiony na powierzchni projektowej widok dokumentu kod znaczników HTML, jak pokazano poniżej:  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Aby uzyskać więcej informacji, zobacz [Div combo](http://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [omówienie kontrolki serwera sieci Web etykiety](http://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac), i <xref:System.Web.UI.WebControls.Label>.  
  
## <a name="see-also"></a>Zobacz też  
 [Przybornik](../../ide/reference/toolbox.md)   
 [Standardowa karta, przybornik](http://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)   
 [Formanty HTML](http://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)
