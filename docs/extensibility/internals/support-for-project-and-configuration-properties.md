---
title: Obsługa projektu i właściwości konfiguracji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0428e2af6e273e961815ec2521ae26afb5e844d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322402"
---
# <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji
**Właściwości** okna [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE) można wyświetlić właściwości projektu i konfiguracji. Strony właściwości można określić dla typu projektu co użytkownik może ustawić właściwości dla aplikacji.

 Wybierając węzeł projektu w **Eksploratora rozwiązań** , a następnie klikając polecenie **właściwości** na **projektu** menu, możesz otworzyć okno dialogowe, które obejmują projektu i konfiguracji właściwości. W [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]i typy pochodzące z tych języków, jako stronę z zakładkami w wyświetlonym oknie dialogowym projektu [ogólne, środowisko, opcje, okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md). Aby uzyskać więcej informacji, zobacz [nie w kompilacji: Przewodnik: Udostępnianie projektów i właściwości konfiguracji (C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Środowiska pakietu zarządzanego dla projektów (MPFProj) udostępnia klasy pomocy do tworzenia i zarządzania nowy system projektów. Instrukcje można znaleźć źródła kodu i kompilacji w [MPF projektów — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Trwałość projektu i właściwości konfiguracji
 Właściwości projektu i konfiguracji są utrwalane w pliku projektu, który ma rozszerzenie nazwy pliku skojarzone z tym typem projektu, na przykład, .csproj, .vbproj i .myproj. Projekty języka zwykle Użyj pliku szablonu do wygenerowania pliku projektu. Jednak istnieją faktycznie na kilka sposobów skojarzenia typów projektów i szablonów. Aby uzyskać więcej informacji, zobacz [opis katalogu szablonu (. Pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Właściwości projektu i konfiguracji są tworzone przez dodanie elementów do pliku szablonu. Te właściwości będą dostępne dla każdego projektu, utworzony przy użyciu typu projektu, który używa tego szablonu. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projekty i MPFProj używają [nie w kompilacji: Przegląd MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) schematu dla plików szablonów. Te pliki zawierają sekcji PropertyGroup dla każdej konfiguracji. Właściwości projektów zwykle są zachowywane w pierwszej sekcji PropertyGroup argumentu konfiguracji jest ustawiony na pusty ciąg.

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
> Projekt można zoptymalizować trwałości przez utrwalanie tylko wartości właściwości, które różnią się od wartości domyślnych.

## <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji
 `Microsoft.VisualStudio.Package.SettingsPage` Klasa implementuje strony właściwości projektu i konfiguracji. Domyślna implementacja klasy `SettingsPage` oferuje właściwości publiczne dla użytkownika w siatce właściwości ogólnych. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Metoda wybiera klasy pochodne `SettingsPage` dla siatki właściwości projektu. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Metoda wybiera klasy pochodne `SettingsPage` dla siatki właściwości konfiguracji. Typu projektu powinny przesłaniać tych metod, aby zaznaczyć odpowiednie właściwości strony.

 `SettingsPage` Klasy i `Microsoft.VisualStudio.Package.ProjectNode` klasy oferują te metody, aby zachować właściwości projektu i konfiguracji:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` i `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` utrwalanie właściwości projektu.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` i `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` utrwalanie właściwości konfiguracji.

  > [!NOTE]
  > Implementacje `Microsoft.VisualStudio.Package.SettingsPage` i `Microsoft.VisualStudio.Package.ProjectNode` klasy użyj `Microsoft.Build.BuildEngine` (MSBuild) metody do pobierania i ustawiania właściwości projektu i konfiguracji z pliku projektu.

  Klasa pochodzi od `SettingsPage` musi implementować `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` i `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` można utrwalić projektu lub konfiguracji właściwości pliku projektu.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute i ścieżki rejestru
 Klasy pochodne `SettingsPage` są przeznaczone do można współdzielić w ramach pakietów VSPackage. Aby umożliwić VSPackage utworzyć klasę pochodną `SettingsPage`, Dodaj `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` do klasy pochodzącej od `Microsoft.VisualStudio.Shell.Package`.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Pakietu VSPackage, do której jest dołączony atrybut nie jest ważna. Gdy pakietu VSPackage jest zarejestrowane w usłudze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], jest zarejestrowany identyfikator klasy (CLSID) dowolnego obiektu, które mogą być tworzone, aby wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> go utworzyć.

 Ścieżka rejestru, obiektu, które mogą być tworzone jest określana przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word, identyfikator CLSID i identyfikator guid typu obiektu. Jeśli `MyProjectPropertyPage` klasa ma identyfikator guid {3c693da2-5bca-49b3-bd95-ffe0a39dd723} UserRegistryRoot jest HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, a następnie byłaby to ścieżka rejestru HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Projekt i atrybuty właściwości konfiguracji i układu
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, I <xref:System.ComponentModel.DescriptionAttribute> atrybuty określają układ, etykietowania i opis właściwości projektu i konfiguracji na stronie właściwości ogólnych. Te atrybuty ustalenia kategorii, nazwę wyświetlaną i opis opcji, odpowiednio.

> [!NOTE]
> Atrybuty równoważne, SRCategory, LocDisplayName i SRDescription, korzystać z zasobów ciągu dla lokalizacji i są definiowane w [MPF projektów — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Rozważmy następujący fragment kodu:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 `MyConfigProp` Właściwość konfiguracji pojawia się na stronie właściwości konfiguracji, co **Moje właściwości konfiguracji** w danej kategorii, **Moje kategorii**. Jeśli wybrano opcję opisu, **Mój opis**, pojawi się na panelu Opis.

## <a name="see-also"></a>Zobacz też
- [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)
- [Projekty](../../extensibility/internals/projects.md)
- [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
