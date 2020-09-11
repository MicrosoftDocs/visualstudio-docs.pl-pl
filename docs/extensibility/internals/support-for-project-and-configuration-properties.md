---
title: Obsługa właściwości projektu i konfiguracji | Microsoft Docs
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
ms.openlocfilehash: be9d9a6e0976ab1ff336fc6754fa44d26c031378
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012025"
---
# <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji
W oknie **Właściwości** w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE) można wyświetlić właściwości projektu i konfiguracji. Możesz podać stronę właściwości dla własnego typu projektu, aby użytkownik mógł ustawić właściwości aplikacji.

 Wybierając węzeł projektu w **Eksplorator rozwiązań** a następnie klikając pozycję **Właściwości** w menu **projekt** , można otworzyć okno dialogowe, w którym znajdują się właściwości projektu i konfiguracji. W programie [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i typów projektów pochodnych od tych języków to okno dialogowe jest wyświetlane jako strona z kartami w [oknie dialogowym ogólne, środowisko, opcje](../../ide/reference/general-environment-options-dialog-box.md). Aby uzyskać więcej informacji, zobacz [nie w kompilacji: Przewodnik: udostępnianie właściwości projektu i konfiguracji (C#)](/previous-versions/bb166517(v=vs.100)).

 Struktura pakietów zarządzanych dla projektów (MPFProj) zapewnia klasy pomocników do tworzenia nowego systemu projektu i zarządzania nim. Kod źródłowy i instrukcje kompilacji można znaleźć pod adresem [MPF for projects — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Trwałość właściwości projektu i konfiguracji
 Właściwości projektu i konfiguracji są utrwalane w pliku projektu, który ma dowolne rozszerzenie nazwy pliku skojarzone z typem projektu, na przykład. csproj,. vbproj i. webproj. Projekty języka zwykle używają pliku szablonu do wygenerowania pliku projektu. Istnieje jednak wiele sposobów kojarzenia typów projektów i szablonów. Aby uzyskać więcej informacji, zobacz [Opis katalogu szablonów (. VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Właściwości projektu i konfiguracji są tworzone przez dodanie elementów do pliku szablonu. Te właściwości są następnie dostępne dla każdego projektu utworzonego za pomocą typu projektu, który używa tego szablonu. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projekty i MPFProj korzystają zarówno z kompilacji, jak i schematu [przeglądu programu MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) dla plików szablonów. Te pliki mają sekcję właściwości dla każdej konfiguracji. Właściwości projektów są zwykle utrwalane w pierwszej sekcji właściwości, która ma argument konfiguracji ustawiony na ciąg o wartości null.

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

 W tym pliku projektu `<Name>` i `<SchemaVersion>` są właściwościami projektu i `<Optimize>` jest właściwością konfiguracji.

 Jest odpowiedzialny za projekt, aby zachować właściwości projektu i konfiguracji pliku projektu.

> [!NOTE]
> Projekt może zoptymalizować trwałość przez utrzymywanie tylko wartości właściwości, które różnią się od wartości domyślnych.

## <a name="support-for-project-and-configuration-properties"></a>Pomoc techniczna dotycząca właściwości projektu i konfiguracji
 `Microsoft.VisualStudio.Package.SettingsPage`Klasa implementuje strony właściwości projektu i konfiguracji. Domyślna implementacja programu `SettingsPage` oferuje właściwości publiczne użytkownikowi w ogólnej siatce właściwości. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`Metoda wybiera klasy pochodne `SettingsPage` dla siatki właściwości projektu. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`Metoda wybiera klasy pochodne od `SettingsPage` dla siatek właściwości konfiguracji. Typ projektu powinien zastąpić te metody, aby wybrać odpowiednie strony właściwości.

 `SettingsPage`Klasa i `Microsoft.VisualStudio.Package.ProjectNode` Klasa oferują te metody, aby zachować właściwości projektu i konfiguracji:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` i `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` utrwalanie właściwości projektu.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` i `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` trwałe właściwości konfiguracji.

  > [!NOTE]
  > Implementacje `Microsoft.VisualStudio.Package.SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` klas i używają `Microsoft.Build.BuildEngine` metod (MSBuild) do pobierania i ustawiania właściwości projektu i konfiguracji z pliku projektu.

  Klasa pochodna `SettingsPage` musi implementować `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` i `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` utrwalać właściwości projektu lub konfiguracji pliku projektu.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute i ścieżka rejestru
 Klasy pochodne `SettingsPage` są przeznaczone do współużytkowania przez pakietów VSPackage. Aby umożliwić pakietu VSPackage Tworzenie klasy pochodzącej od `SettingsPage` , Dodaj `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` do klasy pochodnej z `Microsoft.VisualStudio.Shell.Package` .

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Pakietu VSPackage, do którego atrybut jest dołączony, jest nieważne. Gdy pakietu VSPackage jest zarejestrowany w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , identyfikator klasy (CLSID) dowolnego obiektu, który można utworzyć jest zarejestrowany, aby wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> można było utworzyć.

 Ścieżka rejestru obiektu, który można utworzyć, jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , słowo, identyfikator CLSID i identyfikator GUID typu obiektu. Jeśli `MyProjectPropertyPage` Klasa ma identyfikator GUID {3c693da2-5bca-49b3-bd95-ffe0a39dd723}, a UserRegistryRoot jest HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0Exp, wówczas ścieżka rejestru będzie HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp\clsid \\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Atrybuty i układ właściwości projektu i konfiguracji
 <xref:System.ComponentModel.CategoryAttribute>Atrybuty, <xref:System.ComponentModel.DisplayNameAttribute> i <xref:System.ComponentModel.DescriptionAttribute> określają układ, etykietowanie i opis właściwości projektu i konfiguracji na stronie właściwości ogólnej. Te atrybuty określają odpowiednio kategorię, nazwę wyświetlaną i opis opcji.

> [!NOTE]
> Równoważne atrybuty, SRCategory, LocDisplayName i SRDescription, używają zasobów ciągów do lokalizacji i są zdefiniowane w [MPF dla projektów — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Rozważmy następujący fragment kodu:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 `MyConfigProp`Właściwość konfiguracja jest wyświetlana na stronie właściwości konfiguracja jako **Właściwość moja konfiguracja** w kategorii. **My Category** Jeśli opcja jest zaznaczona, opis, **mój opis**, pojawia się w panelu opisu.

## <a name="see-also"></a>Zobacz także
- [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)
- [Projekty](../../extensibility/internals/projects.md)
- [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)