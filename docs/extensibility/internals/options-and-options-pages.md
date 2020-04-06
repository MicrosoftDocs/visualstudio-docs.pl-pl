---
title: Strony opcji i opcji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706840"
---
# <a name="options-and-options-pages"></a>Opcje i strony opcji
Kliknięcie **przycisku Opcje** w menu **Narzędzia** powoduje otwarcie okna dialogowego **Opcje.** Opcje w tym oknie dialogowym są zbiorczo nazywane opcjami stron. Formant drzewa w okienku nawigacji zawiera kategorie opcji, a każda kategoria ma strony opcji. Po wybraniu strony jej opcje są wyświetlane w prawym okienku. Te strony umożliwiają zmianę wartości opcji, które określają stan VSPackage.

## <a name="support-for-options-pages"></a>Obsługa stron opcji
 Klasa <xref:Microsoft.VisualStudio.Shell.Package> zapewnia obsługę tworzenia stron opcji i kategorii opcji. Klasa <xref:Microsoft.VisualStudio.Shell.DialogPage> implementuje stronę opcji.

 Domyślna implementacja <xref:Microsoft.VisualStudio.Shell.DialogPage> oferuje swoje właściwości publiczne użytkownikowi w ogólnej siatce właściwości. To zachowanie można dostosować, zastępując różne metody na stronie, aby utworzyć stronę opcji niestandardowych, która ma własny interfejs użytkownika (UI). Aby uzyskać więcej informacji, zobacz [Tworzenie strony opcji](../../extensibility/creating-an-options-page.md).

 Klasa <xref:Microsoft.VisualStudio.Shell.DialogPage> implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager>, który zapewnia trwałość dla stron opcji, a także dla ustawień użytkownika. Domyślne implementacje <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> i metody utrwalają zmiany właściwości w sekcji użytkownika rejestru, jeśli właściwość może być konwertowana do i z ciągu.

## <a name="options-page-registry-path"></a>Ścieżka rejestru strony opcje
 Domyślnie ścieżka rejestru właściwości zarządzanych przez stronę opcji jest <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>określana przez połączenie , słowa DialogPage i nazwy typu klasy strony opcji. Na przykład klasa strony opcji może być zdefiniowana w następujący sposób.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Jeśli <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> jest HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, nazwa właściwości i pary wartości są podkluczami HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Ścieżka rejestru strony opcji zależy od połączenia <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, słowo, ToolsOptionsPages, a opcje strony kategorii i nazwy. Jeśli na przykład strona Opcji niestandardowych ma kategorię Moje <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> strony opcji i jest HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, strona opcji ma klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Atrybuty i układ strony narzędzia/opcje
 Atrybut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> określa grupowanie stron opcji niestandardowych na kategorie w drzewie nawigacji w oknie dialogowym **Opcje.** Atrybut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> kojarzy stronę opcji z VSPackage, który udostępnia interfejs. Rozważmy następujący fragment kodu:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Oznacza to, że MyPackage udostępnia dwie strony opcji, OptionsPageGeneral i OptionsPageCustom. W oknie dialogowym **Opcje** obie strony opcji są wyświetlane w kategorii **Moje strony opcji** odpowiednio jako **ogólne** i **niestandardowe.**

## <a name="option-attributes-and-layout"></a>Atrybuty opcji i układ
 Interfejs użytkownika (UI), który zawiera stronę określa wygląd opcji na stronie opcji niestandardowych. Układ, etykietowanie i opis opcji na stronie opcji ogólnych są określane przez następujące atrybuty:

- <xref:System.ComponentModel.CategoryAttribute>określa kategorię opcji.

- <xref:System.ComponentModel.DisplayNameAttribute>określa wyświetlaną nazwę opcji.

- <xref:System.ComponentModel.DescriptionAttribute>określa opis opcji.

  > [!NOTE]
  > Równoważne atrybuty, Kategoria SR, LocDisplayName i SRDescription, użyj zasobów ciągów do lokalizacji i są zdefiniowane w [próbce zarządzanego projektu](/azure/devops/integrate/index).

  Rozważmy następujący fragment kodu:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Opcja OptionInteger jest wyświetlana na stronie opcji jako **opcja całkowita** w kategorii **Moje opcje.** Jeśli opcja jest zaznaczona, w polu opisu moja liczba całkowita pojawi się opis: **Moja liczba całkowita.**

## <a name="accessing-options-pages-from-another-vspackage"></a>Uzyskiwanie dostępu do stron opcji z innego pakietu VSPackage
 VsPackage, który obsługuje i zarządza stronę opcji mogą być programowo dostępne z innego VSPackage przy użyciu modelu automatyzacji. Na przykład w poniższym kodzie VSPackage jest zarejestrowany jako strona z opcją.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Następujący fragment kodu pobiera wartość OptionInteger z MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Gdy <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atrybut rejestruje stronę opcji, strona jest zarejestrowana w kluczu `SupportsAutomation` AutomationProperties, `true`jeśli argument atrybutu jest . Automatyzacja sprawdza ten wpis rejestru, aby znaleźć skojarzony VSPackage, a następnie automatyzacji uzyskuje dostęp do właściwości za pośrednictwem hostowanych opcji strony, w tym przypadku, Moja strona siatki.

 Ścieżka rejestru właściwości automatyzacji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, słowo, AutomationProperties i kategorii strony opcji i nazwy. Jeśli na przykład strona opcji ma kategorię Moja kategoria, nazwę strony <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>Moja siatka i , HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, właściwość automatyzacji ma klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\8.0Exp\AutomationProperties\Moja kategoria\Moja siatka.

> [!NOTE]
> Nazwa kanoniczna My Category.My Grid Page jest wartością podklucza Nazwa tego klucza.
