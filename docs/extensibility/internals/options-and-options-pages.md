---
title: Strony opcji i | Microsoft Docs
description: Dowiedz się więcej na temat obsługi stron opcji, które umożliwiają zmianę wartości opcji, które określają stan pakietów VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea05e894c0bfca077f1256c35e6fbe5c58bc91ea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899891"
---
# <a name="options-and-options-pages"></a>Opcje i strony opcji
Kliknięcie **pozycji** Opcje **w** menu Narzędzia powoduje otwarcie **okna dialogowego** Opcje. Opcje w tym oknie dialogowym są zbiorczo nazywane stronami opcji. Kontrolka drzewa w okienku nawigacji zawiera kategorie opcji, a każda kategoria ma strony opcji. Po wybraniu strony jej opcje są wyświetlane w okienku po prawej stronie. Te strony umożliwiają zmianę wartości opcji, które określają stan pakietów VSPackage.

## <a name="support-for-options-pages"></a>Obsługa stron opcji
 Klasa <xref:Microsoft.VisualStudio.Shell.Package> zapewnia obsługę tworzenia stron opcji i kategorii opcji. Klasa <xref:Microsoft.VisualStudio.Shell.DialogPage> implementuje stronę opcji.

 Domyślna <xref:Microsoft.VisualStudio.Shell.DialogPage> implementacja obiektu udostępnia użytkownikowi właściwości publiczne w ogólnej siatce właściwości. To zachowanie można dostosować, przesłaniając różne metody na stronie, aby utworzyć stronę opcji niestandardowych, która ma własny interfejs użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie strony opcji](../../extensibility/creating-an-options-page.md).

 Klasa <xref:Microsoft.VisualStudio.Shell.DialogPage> implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager> klasę , która zapewnia trwałość stron opcji, a także ustawień użytkownika. Domyślne implementacje metod i utrwalają zmiany właściwości w sekcji użytkownika rejestru, jeśli właściwość może zostać przekonwertowana na ciąg <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> i z ciągu.

## <a name="options-page-registry-path"></a>Ścieżka rejestru stron opcji
 Domyślnie ścieżka rejestru właściwości zarządzanych przez stronę opcji jest określana przez połączenie słowa DialogPage i nazwy typu <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> klasy strony opcji. Na przykład klasę strony opcji można zdefiniować w następujący sposób.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet1":::

 Jeśli wartość HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, pary nazwa właściwości i wartość są <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> podkluczami HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Ścieżka rejestru strony opcji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , wyrazu, narzędziOptionsPages oraz kategorii i nazwy strony opcji. Jeśli na przykład strona Opcje niestandardowe ma kategorię Moje strony opcji, a wartość HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, strona opcji zawiera klucz <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Atrybuty i układ strony narzędzi/opcji
 Atrybut określa grupowanie stron opcji niestandardowych w kategorie w drzewie nawigacji okna <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> **dialogowego** Opcje. Atrybut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> kojarzy stronę opcji z pakietem VSPackage, który udostępnia interfejs. Rozważmy następujący fragment kodu:

:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet2":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet2":::

 Oznacza to, że pakiet MyPackage udostępnia dwie strony opcji: OptionsPageGeneral i OptionsPageCustom. W **oknie dialogowym** Opcje obie strony opcji są  wyświetlane odpowiednio w kategorii **Moje strony** opcji jako Ogólne i Niestandardowe.

## <a name="option-attributes-and-layout"></a>Atrybuty opcji i układ
 Interfejs użytkownika (UI) zapewniany przez stronę określa wygląd opcji na stronie opcji niestandardowych. Układ, etykietowanie i opis opcji na stronie opcji ogólnych są określane przez następujące atrybuty:

- <xref:System.ComponentModel.CategoryAttribute> Określa kategorię opcji.

- <xref:System.ComponentModel.DisplayNameAttribute> Określa nazwę wyświetlaną opcji.

- <xref:System.ComponentModel.DescriptionAttribute> Określa opis opcji.

  > [!NOTE]
  > Równoważne atrybuty, SRCategory, LocDisplayName i SRDescription, używają zasobów ciągu do lokalizacji i są zdefiniowane w [przykładowym projekcie zarządzanym](/azure/devops/integrate/index).

  Rozważmy następujący fragment kodu:

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs" id="Snippet3":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb" id="Snippet3":::

  Opcja OptionInteger jest wyświetlana na stronie opcji jako **Opcja liczby całkowitej** w **kategorii Moje** opcje. Jeśli ta opcja jest zaznaczona, w polu opisu zostanie wyświetlony opis Moja liczba **całkowita.**

## <a name="accessing-options-pages-from-another-vspackage"></a>Uzyskiwanie dostępu do stron opcji z innego pakietów VSPackage
 Pakiet VSPackage, który hostuje stronę opcji i zarządza jej stroną, jest dostępny programowo z innego narzędzia VSPackage przy użyciu modelu automatyzacji. Na przykład w poniższym kodzie pakiet VSPackage jest zarejestrowany jako host strony opcji.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet4":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet4":::

 Poniższy fragment kodu pobiera wartość OptionInteger z myOptionPage:

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet5":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet5":::

 Gdy atrybut rejestruje stronę opcji, strona jest rejestrowana w kluczu <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> AutomationProperties, jeśli `SupportsAutomation` argumentem atrybutu jest `true` . Usługa Automation sprawdza ten wpis rejestru, aby znaleźć skojarzony pakiet VSPackage, a następnie uzyskuje dostęp do właściwości za pośrednictwem hostowanej strony opcji, w tym przypadku strony Siatki.

 Ścieżka rejestru właściwości automatyzacji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , wyrazu AutomationProperties oraz kategorii i nazwy strony opcji. Jeśli na przykład strona opcji ma kategorię Moja kategoria, nazwę mojej strony siatki i HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp , właściwość automatyzacji ma klucz <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> Nazwa kanonicna, Moja Category.My Grid Page, jest wartością podklucza Name tego klucza.
