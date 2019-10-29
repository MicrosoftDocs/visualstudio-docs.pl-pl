---
title: Opcje i strony opcji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 963a73a3a8e079b2171c88e901913990892715cd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981901"
---
# <a name="options-and-options-pages"></a>Opcje i strony opcji
Kliknięcie przycisku **Opcje** w menu **Narzędzia** powoduje otwarcie okna dialogowego **Opcje** . Opcje w tym oknie dialogowym są określane zbiorczo jako strony opcji. Kontrolka drzewa w okienku nawigacji zawiera kategorie opcji, a każda kategoria zawiera strony opcji. Po wybraniu strony opcje są wyświetlane w okienku po prawej stronie. Te strony umożliwiają zmianę wartości opcji, które określają stan pakietu VSPackage.

## <a name="support-for-options-pages"></a>Obsługa stron opcji
 Klasa <xref:Microsoft.VisualStudio.Shell.Package> zapewnia obsługę tworzenia stron opcji i kategorii opcji. Klasa <xref:Microsoft.VisualStudio.Shell.DialogPage> implementuje stronę opcji.

 Domyślna implementacja <xref:Microsoft.VisualStudio.Shell.DialogPage> oferuje jej właściwości publiczne użytkownikowi w ogólnej siatce właściwości. To zachowanie można dostosować, zastępując różne metody na stronie w celu utworzenia strony opcji niestandardowych, która ma własny interfejs użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie strony opcji](../../extensibility/creating-an-options-page.md).

 Klasa <xref:Microsoft.VisualStudio.Shell.DialogPage> implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager>, która zapewnia trwałość dla stron opcji, a także dla ustawień użytkownika. Domyślne implementacje metod <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> i <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> utrzymują zmiany właściwości w sekcji użytkownika rejestru, jeśli właściwość może zostać przekonwertowana na i z ciągu.

## <a name="options-page-registry-path"></a>Strona opcji Ścieżka rejestru
 Domyślnie ścieżka rejestru właściwości zarządzanych przez stronę opcji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, słowa typu DialogPage oraz nazwy typu klasy strony opcji. Na przykład Klasa strony opcji może być zdefiniowana w następujący sposób.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Jeśli <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> to HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, a następnie nazwa właściwości i pary wartości są podkluczami HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Ścieżka rejestru samej strony opcji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, słowo, ToolsOptionsPages oraz kategorię i nazwę strony opcji. Na przykład jeśli strona Opcje niestandardowe zawiera kategorię, moje strony opcji, a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, a następnie strona Opcje ma klucz rejestru, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\ 8.0 EXP \ ToolsOptionsPages \ Moja opcja Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Narzędzia/Opcje strony — atrybuty i układ
 Atrybut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> określa grupowanie stron opcji niestandardowych w kategorii w drzewie nawigacji okna dialogowego **Opcje** . Atrybut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> kojarzy stronę opcji z pakietu VSPackage, która dostarcza interfejs. Rozważmy następujący fragment kodu:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Deklaruje, że pakiet webpackage udostępnia dwie strony opcji, OptionsPageGeneral i OptionsPageCustom. W oknie dialogowym **Opcje** obie strony opcji są wyświetlane w kategorii **Moje** opcje jako **Ogólne** i **niestandardowe**odpowiednio.

## <a name="option-attributes-and-layout"></a>Atrybuty i układ opcji
 Interfejs użytkownika, który zawiera strona określa wygląd opcji na stronie opcji niestandardowych. Układ, etykietowanie i opis opcji na stronie opcji ogólnych są określane przez następujące atrybuty:

- <xref:System.ComponentModel.CategoryAttribute> Określa kategorię opcji.

- <xref:System.ComponentModel.DisplayNameAttribute> określa nazwę wyświetlaną opcji.

- <xref:System.ComponentModel.DescriptionAttribute> określa opis opcji.

  > [!NOTE]
  > Równoważne atrybuty, SRCategory, LocDisplayName i SRDescription, służą do lokalizowania zasobów ciągów i są zdefiniowane w [próbce projektu zarządzanego](/azure/devops/integrate/index).

  Rozważmy następujący fragment kodu:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Opcja OptionInteger jest wyświetlana na stronie Opcje jako **Liczba całkowita** w kategorii **My Options** . Jeśli opcja jest zaznaczona, w polu Opis zostanie wyświetlona opcja Opis, **My Integer**.

## <a name="accessing-options-pages-from-another-vspackage"></a>Dostęp do stron opcji z innego pakietu VSPackage
 Pakietu VSPackage, który hostuje i zarządza stroną opcji można programistycznie uzyskać dostęp z innego pakietu VSPackage przy użyciu modelu automatyzacji. Na przykład w poniższym kodzie pakietu VSPackage jest zarejestrowana jako hostowanie strony opcji.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Poniższy fragment kodu pobiera wartość OptionInteger z MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Gdy atrybut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> rejestruje stronę opcji, strona jest zarejestrowana w kluczu AutomationProperties, jeśli argument `SupportsAutomation` atrybutu jest `true`. Usługa Automation analizuje ten wpis rejestru, aby znaleźć skojarzone pakietu VSPackage, a następnie usługa Automation uzyskuje dostęp do właściwości za pomocą strony Opcje hostowane, w tym przypadku strony Moje siatki.

 Ścieżka rejestru właściwości automatyzacji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, wyrazów, AutomationProperties oraz kategorii i nazwy strony opcji. Na przykład, jeśli strona opcji zawiera kategorię my Category, nazwa strony My Grid i <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, a następnie właściwość Automation ma klucz rejestru, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Strona siatki VisualStudio\8.0Exp\AutomationProperties\My Category\My.

> [!NOTE]
> Nazwa kanoniczna, Strona Category.My Grid, jest wartością podklucza nazwy tego klucza.