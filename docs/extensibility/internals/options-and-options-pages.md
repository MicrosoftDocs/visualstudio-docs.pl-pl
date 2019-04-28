---
title: Opcje i strony opcji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db221c99b90f99f80c89f504281be4233ce3a046
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424207"
---
# <a name="options-and-options-pages"></a>Opcje i strony opcji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Klikając **opcje** na **narzędzia** zostanie otwarte menu **opcje** okno dialogowe. Opcje w oknie dialogowym są zbiorczo określany jako opcje strony. Drzewie w okienku nawigacji zawiera opcje kategorie, a każda kategoria ma stron opcji. Po wybraniu strony, dostępne opcje są wyświetlane w okienku po prawej stronie. Te strony umożliwiają zmienić wartości opcji, które określają stan pakietu VSPackage.  
  
## <a name="support-for-options-pages"></a>Obsługa stron opcji  
 <xref:Microsoft.VisualStudio.Shell.Package> Klasy zapewnia obsługę tworzenia stron opcji i opcje kategorii. <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasa implementuje stronę opcji.  
  
 Domyślna implementacja klasy <xref:Microsoft.VisualStudio.Shell.DialogPage> oferuje jego właściwości publiczne użytkownikowi ogólnego siatki właściwości. To zachowanie można dostosować poprzez zastąpienie różne metody, na stronie, aby utworzyć stronę opcji niestandardowych, która ma własny interfejs użytkownika (UI). Aby uzyskać więcej informacji, zobacz [Tworzenie strony opcji](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasy implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager>, zapewniającą stanów trwałych dla stron opcji, a także dla ustawień użytkownika. Domyślna implementacja metody <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> i <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> metody utrwala zmiany właściwości użytkownika części rejestru, jeśli właściwości mogą być konwertowane do i z ciągu.  
  
## <a name="options-page-registry-path"></a>Ścieżka rejestru strony opcji  
 Domyślnie, ścieżka rejestru właściwości zarządzane przez stronę opcji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word typu DialogPage i nazwę typu klasy strony opcje. Na przykład klasy strony opcji może być zdefiniowana w następujący sposób.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Jeśli <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> jest HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, pary nazw i wartości właściwości są podkluczy HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Ścieżka rejestru sama strona Opcje jest określana przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, wyraz, ToolsOptionsPages i opcje strony kategorii i nazwę. Na przykład, jeśli niestandardowy strona opcji posiada kategorii Moje strony opcji, a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> jest HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, Strona opcji posiada HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ klucza rejestru. VisualStudio\8.0Exp\ToolsOptionsPages\My Pages\Custom opcji.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Narzędzia/Opcje atrybutów strony i układu  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Atrybut określa zbiór niestandardowych stron opcji na kategorie w drzewie nawigacji **opcje** okno dialogowe. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Atrybut kojarzy strony opcji za pomocą pakietu VSPackage, który zapewnia interfejs. Rozważmy następujący fragment kodu:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Deklaruje, że MyPackage oferuje dwie opcje strony, OptionsPageGeneral i OptionsPageCustom. W **opcje** okno dialogowe, obie strony opcje są wyświetlane w **Moje strony opcji** kategorii co **ogólne** i **niestandardowe**, odpowiednio.  
  
## <a name="option-attributes-and-layout"></a>Opcja atrybutów i układu  
 Interfejs użytkownika (UI), który zawiera strony określa wygląd opcje na stronie Opcje niestandardowe. Układ, etykietowania i opis opcji na stronie opcji ogólnych są określane przez następujące atrybuty:  
  
- <xref:System.ComponentModel.CategoryAttribute> Określa kategorię opcji.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> Określa nazwę wyświetlaną opcji.  
  
- <xref:System.ComponentModel.DescriptionAttribute> Określa opis opcji.  
  
  > [!NOTE]
  > Atrybuty równoważne, SRCategory, LocDisplayName i SRDescription, korzystać z zasobów ciągu dla lokalizacji i są definiowane w [przykładowym projekcie zarządzanych](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
  Rozważmy następujący fragment kodu:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  Opcja OptionInteger pojawia się na stronie Opcje jako **opcji całkowitą** w **Moje opcje** kategorii. Jeśli wybrano opcję opisu, **Moje opcji całkowitą**, jest wyświetlany w polu opisu.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Uzyskiwanie dostępu do stron opcji z innego pakietu VSPackage  
 Pakietu VSPackage, który hostuje i zarządza strony opcji programowo możliwy od innego pakietu VSPackage przy użyciu modelu automatyzacji. Na przykład w poniższym kodzie pakietu VSPackage jest zarejestrowany jako stanowiącego host strony opcji.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Poniższy fragment kodu pobiera wartość OptionInteger z MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Gdy <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atrybut rejestruje Strona opcji, strona jest zarejestrowany w obszarze Jeśli klucza AutomationProperties `SupportsAutomation` argument atrybutu jest `true`. Automatyzacja sprawdza, czy ten wpis rejestru, aby znaleźć skojarzonego pakietu VSPackage i automatyzacji, a następnie uzyskuje dostęp do właściwości przy użyciu hostowanego Strona opcji, w tym przypadku Moje strony siatki.  
  
 Ścieżka rejestru właściwości automatyzacji jest określana przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, wyraz, AutomationProperties i opcje strony kategorii i nazwę. Na przykład, jeśli strona opcji posiada kategorii Moje kategorii, nazwę Moje strony siatki i <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, a następnie właściwość automatyzacji zawiera klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\ Strona siatki Category\My Microsoft\VisualStudio\8.0Exp\AutomationProperties\My.  
  
> [!NOTE]
> Nazwa kanoniczna Moje Category.My stronie siatki, to wartość podklucza nazwę tego klucza.
