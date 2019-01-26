---
title: Opcje i strony opcji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 466dc5ea2c3ca4a4f9045a43781598c7e84168ba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930042"
---
# <a name="options-and-options-pages"></a>Opcje i strony opcji
Klikając **opcje** na **narzędzia** zostanie otwarte menu **opcje** okno dialogowe. Opcje w oknie dialogowym są zbiorczo określany jako opcje strony. Drzewie w okienku nawigacji zawiera opcje kategorie, a każda kategoria ma stron opcji. Po wybraniu strony, dostępne opcje są wyświetlane w okienku po prawej stronie. Te strony umożliwiają zmienić wartości opcji, które określają stan pakietu VSPackage.  
  
## <a name="support-for-options-pages"></a>Obsługa stron opcji  
 <xref:Microsoft.VisualStudio.Shell.Package> Klasy zapewnia obsługę tworzenia stron opcji i opcje kategorii. <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasa implementuje stronę opcji.  
  
 Domyślna implementacja klasy <xref:Microsoft.VisualStudio.Shell.DialogPage> oferuje jego właściwości publiczne użytkownikowi ogólnego siatki właściwości. To zachowanie można dostosować poprzez zastąpienie różne metody, na stronie, aby utworzyć stronę opcji niestandardowych, która ma własny interfejs użytkownika (UI). Aby uzyskać więcej informacji, zobacz [Tworzenie strony opcji](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasy implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager>, zapewniającą stanów trwałych dla stron opcji, a także dla ustawień użytkownika. Domyślna implementacja metody <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> i <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> metody utrwala zmiany właściwości użytkownika części rejestru, jeśli właściwości mogą być konwertowane do i z ciągu.  
  
## <a name="options-page-registry-path"></a>Ścieżka rejestru strony opcji  
 Domyślnie, ścieżka rejestru właściwości zarządzane przez stronę opcji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word typu DialogPage i nazwę typu klasy strony opcje. Na przykład klasy strony opcji może być zdefiniowana w następujący sposób.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Jeśli <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> jest HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, pary nazw i wartości właściwości są podkluczy HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Ścieżka rejestru sama strona Opcje jest określana przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, wyraz, ToolsOptionsPages i opcje strony kategorii i nazwę. Na przykład, jeśli niestandardowy strona opcji posiada kategorii Moje strony opcji, a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> jest HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, Strona opcji posiada HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ klucza rejestru. VisualStudio\8.0Exp\ToolsOptionsPages\My Pages\Custom opcji.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Narzędzia/Opcje atrybutów strony i układu  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Atrybut określa zbiór niestandardowych stron opcji na kategorie w drzewie nawigacji **opcje** okno dialogowe. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Atrybut kojarzy strony opcji za pomocą pakietu VSPackage, który zapewnia interfejs. Rozważmy następujący fragment kodu:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Deklaruje, że MyPackage oferuje dwie opcje strony, OptionsPageGeneral i OptionsPageCustom. W **opcje** okno dialogowe, obie strony opcje są wyświetlane w **Moje strony opcji** kategorii co **ogólne** i **niestandardowe**, odpowiednio.  
  
## <a name="option-attributes-and-layout"></a>Opcja atrybutów i układu  
 Interfejs użytkownika (UI), który zawiera strony określa wygląd opcje na stronie Opcje niestandardowe. Układ, etykietowania i opis opcji na stronie opcji ogólnych są określane przez następujące atrybuty:  
  
- <xref:System.ComponentModel.CategoryAttribute> Określa kategorię opcji.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> Określa nazwę wyświetlaną opcji.  
  
- <xref:System.ComponentModel.DescriptionAttribute> Określa opis opcji.  
  
  > [!NOTE]
  >  Atrybuty równoważne, SRCategory, LocDisplayName i SRDescription, korzystać z zasobów ciągu dla lokalizacji i są definiowane w [przykładowym projekcie zarządzanych](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
  Rozważmy następujący fragment kodu:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
  Opcja OptionInteger pojawia się na stronie Opcje jako **opcji całkowitą** w **Moje opcje** kategorii. Jeśli wybrano opcję opisu, **Moje opcji całkowitą**, jest wyświetlany w polu opisu.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Uzyskiwanie dostępu do stron opcji z innego pakietu VSPackage  
 Pakietu VSPackage, który hostuje i zarządza strony opcji programowo możliwy od innego pakietu VSPackage przy użyciu modelu automatyzacji. Na przykład w poniższym kodzie pakietu VSPackage jest zarejestrowany jako stanowiącego host strony opcji.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 Poniższy fragment kodu pobiera wartość OptionInteger z MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Gdy <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atrybut rejestruje Strona opcji, strona jest zarejestrowany w obszarze Jeśli klucza AutomationProperties `SupportsAutomation` argument atrybutu jest `true`. Automatyzacja sprawdza, czy ten wpis rejestru, aby znaleźć skojarzonego pakietu VSPackage i automatyzacji, a następnie uzyskuje dostęp do właściwości przy użyciu hostowanego Strona opcji, w tym przypadku Moje strony siatki.  
  
 Ścieżka rejestru właściwości automatyzacji jest określana przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, wyraz, AutomationProperties i opcje strony kategorii i nazwę. Na przykład, jeśli strona opcji posiada kategorii Moje kategorii, nazwę Moje strony siatki i <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, a następnie właściwość automatyzacji zawiera klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\ Strona siatki Category\My Microsoft\VisualStudio\8.0Exp\AutomationProperties\My.  
  
> [!NOTE]
>  Nazwa kanoniczna Moje Category.My stronie siatki, to wartość podklucza nazwę tego klucza.