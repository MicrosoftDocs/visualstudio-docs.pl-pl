---
title: Obsługa właściwości projektu i konfiguracji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704899"
---
# <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji
Okno **Właściwości** w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE) może wyświetlać właściwości projektu i konfiguracji. Można podać stronę właściwości dla własnego typu projektu, dzięki czemu użytkownik może ustawić właściwości aplikacji.

 Wybierając węzeł projektu w **Eksploratorze** **rozwiązań,** a następnie klikając polecenie Właściwości w menu **Projekt,** można otworzyć okno dialogowe zawierające właściwości projektu i konfiguracji. W [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]przypadku typów projektów i typów projektów pochodzących z tych języków to okno dialogowe jest wyświetlane jako strona z kartami w [oknie dialogowym Ogólne, Środowisko i Opcje](../../ide/reference/general-environment-options-dialog-box.md). Aby uzyskać więcej informacji, zobacz [Nie w kompilacji: Instruktaż: Udostępnianie właściwości projektu i konfiguracji (C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Struktura pakietu zarządzanego dla projektów (MPFProj) zapewnia klasy pomocnicze do tworzenia i zarządzania nowym systemem projektów. Kod źródłowy i instrukcje kompilacji można znaleźć w [mpf dla projektów — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Trwałość właściwości projektu i konfiguracji
 Właściwości projektu i konfiguracji są zachowywane w pliku projektu, który ma dowolne rozszerzenie nazwy pliku skojarzone z typem projektu, na przykład .csproj, .vbproj i .myproj. Projekty językowe zazwyczaj używają pliku szablonu do wygenerowania pliku projektu. Jednak w rzeczywistości istnieje kilka sposobów kojarzenia typów projektów i szablonów. Aby uzyskać więcej informacji, zobacz [Opis katalogu szablonów (. Vsdir) Pliki](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Właściwości projektu i konfiguracji są tworzone przez dodanie elementów do pliku szablonu. Te właściwości są następnie dostępne dla każdego projektu utworzonego przy użyciu typu projektu, który używa tego szablonu. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]zarówno projekty, jak i MPFProj używają schematu [Nie w kompilacji: PRZEGLĄD MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) dla plików szablonów. Te pliki mają sekcję PropertyGroup dla każdej konfiguracji. Właściwości projektów są zazwyczaj utrwalone w pierwszej sekcji PropertyGroup, która ma argument Configuration ustawiony na ciąg zerowy.

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

 W tym pliku `<Name>` `<SchemaVersion>` projektu i są `<Optimize>` właściwości projektu i jest właściwością konfiguracji.

 Jest odpowiedzialny za projekt do utrwalenia właściwości projektu i konfiguracji pliku projektu.

> [!NOTE]
> Projekt można zoptymalizować trwałość przez utrwalanie tylko wartości właściwości, które różnią się od ich wartości domyślnych.

## <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji
 Klasa `Microsoft.VisualStudio.Package.SettingsPage` implementuje strony właściwości projektu i konfiguracji. Domyślna implementacja `SettingsPage` oferuje właściwości publiczne dla użytkownika w ogólnej siatce właściwości. Metoda `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` wybiera klasy pochodne `SettingsPage` dla siatki właściwości projektu. Metoda `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` wybiera klasy uzyskane `SettingsPage` z dla siatki właściwości konfiguracji. Typ projektu należy zastąpić te metody, aby wybrać odpowiednie strony właściwości.

 Klasa `SettingsPage` i `Microsoft.VisualStudio.Package.ProjectNode` klasa oferują te metody, aby utrzymywać właściwości projektu i konfiguracji:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`i `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` utrwalać właściwości projektu.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`i `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` utrwalać właściwości konfiguracji.

  > [!NOTE]
  > Implementacje `Microsoft.VisualStudio.Package.SettingsPage` i `Microsoft.VisualStudio.Package.ProjectNode` klasy używają `Microsoft.Build.BuildEngine` (MSBuild) metody, aby uzyskać i ustawić właściwości projektu i konfiguracji z pliku projektu.

  Klasa, z `SettingsPage` której pochodzisz, musi zostać zaimplementowana `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` i `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` utrzymywać właściwości projektu lub konfiguracji pliku projektu.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute i ścieżka rejestru
 Klasy pochodzące `SettingsPage` z są przeznaczone do udostępniania w VSPackages. Aby umożliwić vspackage utworzyć klasę pochodną , `SettingsPage`dodaj `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` do klasy pochodną `Microsoft.VisualStudio.Shell.Package`.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 VSPackage, do którego dołączony jest atrybut jest nieważny. Gdy VSPackage jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zarejestrowany w programie , identyfikator klasy (CLSID) dowolnego obiektu, który <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> można utworzyć jest zarejestrowany, tak aby wywołanie można utworzyć.

 Ścieżka rejestru obiektu, który można utworzyć, jest <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>określana przez połączenie wyrazu, identyfikatora CLSID i identyfikatora guid typu obiektu. Jeśli `MyProjectPropertyPage` klasa ma identyfikator {3c693da2-5bca-49b3-bd95-ffe0a39dd723}, a UserRegistryRoot jest HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, następnie ścieżka rejestru będzie HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Atrybuty i układ właściwości projektu i konfiguracji
 <xref:System.ComponentModel.CategoryAttribute>Atrybuty <xref:System.ComponentModel.DisplayNameAttribute>, <xref:System.ComponentModel.DescriptionAttribute> i atrybuty określają układ, etykietowanie i opis właściwości projektu i konfiguracji na stronie właściwości ogólnego. Te atrybuty określają odpowiednio kategorię, nazwę wyświetlaną i opis opcji.

> [!NOTE]
> Równoważne atrybuty, Kategoria SR, LocDisplayName i SRDescription, użyj zasobów ciągów do lokalizacji i są zdefiniowane w [MPF dla projektów — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Rozważmy następujący fragment kodu:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 Właściwość `MyConfigProp` konfiguracji pojawia się na stronie właściwości konfiguracji jako **Właściwość Moja konfiguracja** w kategorii **Moja kategoria**. Jeśli opcja jest zaznaczona, w panelu opisu pojawi się opis **Mój opis.**

## <a name="see-also"></a>Zobacz też
- [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)
- [Projekty](../../extensibility/internals/projects.md)
- [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
