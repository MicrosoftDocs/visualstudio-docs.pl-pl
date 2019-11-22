---
title: Obsługa właściwości projektu i konfiguracji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b03bc04b1d5b87219110aa65bee53c4a4a8f77e2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301072"
---
# <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W oknie **Właściwości** w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE) można wyświetlić właściwości projektu i konfiguracji. Możesz podać stronę właściwości dla własnego typu projektu, aby użytkownik mógł ustawić właściwości aplikacji.  
  
 Wybierając węzeł projektu w **Eksplorator rozwiązań** a następnie klikając pozycję **Właściwości** w menu **projekt** , można otworzyć okno dialogowe, w którym znajdują się właściwości projektu i konfiguracji. W [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]i typów projektów pochodnych od tych języków to okno dialogowe jest wyświetlane jako strona z kartami w [oknie dialogowym ogólne, środowisko, opcje](../../ide/reference/general-environment-options-dialog-box.md). Aby uzyskać więcej informacji, zobacz [nie w kompilacji: Przewodnik: udostępnianie właściwości projektu i konfiguracjiC#()](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Struktura pakietów zarządzanych dla projektów (MPFProj) zapewnia klasy pomocników do tworzenia nowego systemu projektu i zarządzania nim. Kod źródłowy i instrukcje kompilacji można znaleźć pod adresem [MPF for projects — Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Trwałość właściwości projektu i konfiguracji  
 Właściwości projektu i konfiguracji są utrwalane w pliku projektu, który ma rozszerzenie nazwy pliku skojarzone z typem projektu, na przykład. csproj,. vbproj i. webproj. Projekty języka zwykle używają pliku szablonu do wygenerowania pliku projektu. Istnieje jednak wiele sposobów kojarzenia typów projektów i szablonów. Aby uzyskać więcej informacji, zobacz [NIB: szablony programu Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) i [Opis katalogu szablonów (. VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Właściwości projektu i konfiguracji są tworzone przez dodanie elementów do pliku szablonu. Te właściwości są następnie dostępne dla każdego projektu utworzonego za pomocą typu projektu, który używa tego szablonu. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projekty i MPFProj używają zarówno szablonu [nieznajdującego się w kompilacji: schemat przeglądu programu MSBuild](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) dla plików szablonów. Te pliki mają sekcję właściwości dla każdej konfiguracji. Właściwości projektów są zwykle utrwalane w pierwszej sekcji właściwości, która ma argument konfiguracji ustawiony na ciąg o wartości null.  
  
 Poniższy kod przedstawia początek podstawowego pliku projektu MSBuild.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 W tym pliku projektu `<Name>` i `<SchemaVersion>` są właściwościami projektu, a `<Optimize>` jest właściwością konfiguracji.  
  
 Jest odpowiedzialny za projekt, aby zachować właściwości projektu i konfiguracji pliku projektu.  
  
> [!NOTE]
> Projekt może zoptymalizować trwałość przez utrzymywanie tylko wartości właściwości, które różnią się od wartości domyślnych.  
  
## <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji  
 Klasa `Microsoft.VisualStudio.Package.SettingsPage` implementuje strony właściwości projektu i konfiguracji. Domyślna implementacja `SettingsPage` udostępnia właściwości publiczne użytkownikowi w ogólnej siatce właściwości. Metoda `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` wybiera klasy pochodne od `SettingsPage` dla siatek właściwości projektu. Metoda `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` wybiera klasy pochodne od `SettingsPage` dla siatek właściwości konfiguracji. Typ projektu powinien zastąpić te metody, aby wybrać odpowiednie strony właściwości.  
  
 Klasa `SettingsPage` i Klasa `Microsoft.VisualStudio.Package.ProjectNode` oferują te metody, aby zachować właściwości projektu i konfiguracji:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` i `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` utrwalać właściwości projektu.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` i `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` utrwalać właściwości konfiguracji.  
  
  > [!NOTE]
  > Implementacje klas `Microsoft.VisualStudio.Package.SettingsPage` i `Microsoft.VisualStudio.Package.ProjectNode` używają metod `Microsoft.Build.BuildEngine` (MSBuild) do pobierania i ustawiania właściwości projektu i konfiguracji z pliku projektu.  
  
  Klasa, z której pochodzi `SettingsPage`, musi implementować `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` i `Microsoft.VisualStudio.Package.SettingsPage.BindProperties`, aby zachować właściwości projektu lub konfiguracji pliku projektu.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute i ścieżka rejestru  
 Klasy pochodne `SettingsPage` są przeznaczone do współużytkowania przez pakietów VSPackage. Aby umożliwić pakietu VSPackage Tworzenie klasy pochodzącej od `SettingsPage`, Dodaj `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` do klasy pochodnej `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 Pakietu VSPackage, do którego atrybut jest dołączony, jest nieważne. Gdy pakietu VSPackage jest zarejestrowany w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], identyfikator klasy (CLSID) dowolnego obiektu, który może zostać utworzony, jest rejestrowany, aby wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> może go utworzyć.  
  
 Ścieżka rejestru obiektu, który można utworzyć, jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, wyrazu, identyfikatora CLSID i identyfikatora GUID typu obiektu. Jeśli Klasa `MyProjectPropertyPage` ma identyfikator GUID {3c693da2-5bca-49b3-bd95-ffe0a39dd723}, a UserRegistryRoot jest HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp, ścieżka rejestru będzie HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Atrybuty i układ właściwości projektu i konfiguracji  
 Atrybuty <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>i <xref:System.ComponentModel.DescriptionAttribute> określają układ, etykietowanie i opis właściwości projektu i konfiguracji na stronie właściwości ogólnej. Te atrybuty określają odpowiednio kategorię, nazwę wyświetlaną i opis opcji.  
  
> [!NOTE]
> Równoważne atrybuty, SRCategory, LocDisplayName i SRDescription, używają zasobów ciągów do lokalizacji i są zdefiniowane w [MPF dla projektów — Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Rozważmy następujący fragment kodu:  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 Właściwość konfiguracja `MyConfigProp` jest wyświetlana na stronie właściwości konfiguracji jako **Właściwość moja konfiguracja** w **kategorii.** Jeśli opcja jest zaznaczona, opis, **mój opis**, pojawia się w panelu opisu.  
  
## <a name="see-also"></a>Zobacz też  
 [Nie w kompilacji: Przewodnik: udostępnianie właściwości projektu i konfiguracji (C#)](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)   
   [stanu pakietu VSPackage](../../misc/vspackage-state.md)  
   [projektów](../../extensibility/internals/projects.md)  
 [NIB: szablony Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
