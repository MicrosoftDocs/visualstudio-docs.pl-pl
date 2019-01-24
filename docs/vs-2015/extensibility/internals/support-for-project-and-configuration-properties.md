---
title: Obsługa projektu i właściwości konfiguracji | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c4c62bf12505bf04b8a680946ce848ea92709507
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795615"
---
# <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Właściwości** okna [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE) można wyświetlić właściwości projektu i konfiguracji. Strony właściwości można określić dla typu projektu co użytkownik może ustawić właściwości dla aplikacji.  
  
 Wybierając węzeł projektu w **Eksploratora rozwiązań** , a następnie klikając polecenie **właściwości** na **projektu** menu, możesz otworzyć okno dialogowe, które obejmują projektu i konfiguracji właściwości. W [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]i typy pochodzące z tych języków, jako stronę z zakładkami w wyświetlonym oknie dialogowym projektu [ogólne, środowisko, opcje, okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md). Aby uzyskać więcej informacji, zobacz [nie w kompilacji: Przewodnik: Udostępnianie projektów i właściwości konfiguracji (C#)](http://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Środowiska pakietu zarządzanego dla projektów (MPFProj) udostępnia klasy pomocy do tworzenia i zarządzania nowy system projektów. Instrukcje można znaleźć źródła kodu i kompilacji w [MPF projektów — Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Trwałość projektu i właściwości konfiguracji  
 Właściwości projektu i konfiguracji są utrwalane w pliku projektu, który ma rozszerzenie nazwy pliku skojarzone z tym typem projektu, na przykład, .csproj, .vbproj i .myproj. Projekty języka zwykle Użyj pliku szablonu do wygenerowania pliku projektu. Jednak istnieją faktycznie na kilka sposobów skojarzenia typów projektów i szablonów. Aby uzyskać więcej informacji, zobacz [NIB: Szablony programu Visual Studio](http://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) i [opis katalogu szablonu (. Pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Właściwości projektu i konfiguracji są tworzone przez dodanie elementów do pliku szablonu. Te właściwości będą dostępne dla każdego projektu, utworzony przy użyciu typu projektu, który używa tego szablonu. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projekty i MPFProj używają [nie w kompilacji: Przegląd MSBuild](http://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) schematu dla plików szablonów. Te pliki zawierają sekcji PropertyGroup dla każdej konfiguracji. Właściwości projektów zwykle są zachowywane w pierwszej sekcji PropertyGroup argumentu konfiguracji jest ustawiony na pusty ciąg.  
  
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
  
 W tym pliku projektu `<Name>` i `<SchemaVersion>` właściwości projektu i `<Optimize>` to właściwość konfiguracji.  
  
 Jest odpowiedzialny za projekt, aby zachować właściwości projektu i konfiguracji w pliku projektu.  
  
> [!NOTE]
>  Projekt można zoptymalizować trwałości przez utrwalanie tylko wartości właściwości, które różnią się od wartości domyślnych.  
  
## <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji  
 `Microsoft.VisualStudio.Package.SettingsPage` Klasa implementuje strony właściwości projektu i konfiguracji. Domyślna implementacja klasy `SettingsPage` oferuje właściwości publiczne dla użytkownika w siatce właściwości ogólnych. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Metoda wybiera klasy pochodne `SettingsPage` dla siatki właściwości projektu. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Metoda wybiera klasy pochodne `SettingsPage` dla siatki właściwości konfiguracji. Typu projektu powinny przesłaniać tych metod, aby zaznaczyć odpowiednie właściwości strony.  
  
 `SettingsPage` Klasy i `Microsoft.VisualStudio.Package.ProjectNode` klasy oferują te metody, aby zachować właściwości projektu i konfiguracji:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` i `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` utrwalanie właściwości projektu.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` i `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` utrwalanie właściwości konfiguracji.  
  
  > [!NOTE]
  >  Implementacje `Microsoft.VisualStudio.Package.SettingsPage` i `Microsoft.VisualStudio.Package.ProjectNode` klasy użyj `Microsoft.Build.BuildEngine` (MSBuild) metody do pobierania i ustawiania właściwości projektu i konfiguracji z pliku projektu.  
  
  Klasa pochodzi od `SettingsPage` musi implementować `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` i `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` można utrwalić projektu lub konfiguracji właściwości pliku projektu.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute i ścieżki rejestru  
 Klasy pochodne `SettingsPage` są przeznaczone do można współdzielić w ramach pakietów VSPackage. Aby umożliwić VSPackage utworzyć klasę pochodną `SettingsPage`, Dodaj `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` do klasy pochodzącej od `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 Pakietu VSPackage, do której jest dołączony atrybut nie jest ważna. Gdy pakietu VSPackage jest zarejestrowane w usłudze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], jest zarejestrowany identyfikator klasy (CLSID) dowolnego obiektu, które mogą być tworzone, aby wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> go utworzyć.  
  
 Ścieżka rejestru, obiektu, które mogą być tworzone jest określana przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word, identyfikator CLSID i identyfikator guid typu obiektu. Jeśli `MyProjectPropertyPage` klasa ma identyfikator guid {3c693da2-5bca-49b3-bd95-ffe0a39dd723} UserRegistryRoot jest HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, a następnie byłaby to ścieżka rejestru HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Projekt i atrybuty właściwości konfiguracji i układu  
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, I <xref:System.ComponentModel.DescriptionAttribute> atrybuty określają układ, etykietowania i opis właściwości projektu i konfiguracji na stronie właściwości ogólnych. Te atrybuty ustalenia kategorii, nazwę wyświetlaną i opis opcji, odpowiednio.  
  
> [!NOTE]
>  Atrybuty równoważne, SRCategory, LocDisplayName i SRDescription, korzystać z zasobów ciągu dla lokalizacji i są definiowane w [MPF projektów — Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Rozważmy następujący fragment kodu:  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 `MyConfigProp` Właściwość konfiguracji pojawia się na stronie właściwości konfiguracji, co **Moje właściwości konfiguracji** w danej kategorii, **Moje kategorii**. Jeśli wybrano opcję opisu, **Mój opis**, pojawi się na panelu Opis.  
  
## <a name="see-also"></a>Zobacz też  
 [Nie w kompilacji: Przewodnik: Udostępnianie projektów i właściwości konfiguracji (C#)](http://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)   
 [Stan pakietu VSPackage](../../misc/vspackage-state.md)   
 [Projekty](../../extensibility/internals/projects.md)   
 [NIB: Visual Studio Templates](http://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
