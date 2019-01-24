---
title: Obsługa ustawień kategorii | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: jillfra
ms.openlocfilehash: b37fe476c7654cc21a3b81f4a68aa4abc0348bb1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766271"
---
# <a name="support-for-settings-categories"></a>Obsługa ustawień kategorii
Kategoria Ustawienia składa się z grupą opcje umożliwiające dostosowanie zintegrowanego środowiska programistycznego (IDE). Na przykład ustawienia można kontrolować układ [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] systemów windows i zawartość elementu menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Na **narzędzia** kliknij menu **Import i eksport ustawień** można uruchomić **Kreatora importowania i eksportowania ustawień**. Kreator udostępnia trzy opcje: eksportowanie, zaimportować lub zresetowanie ustawień programu. Na przykład wybranie eksportu, otwiera **wybierz ustawienia do eksportowania** strony kreatora.  
  
 Kontrolka drzewa w okienku nawigacji strony Wyświetla listę kategorii. Kategoria jest grupą powiązanych ustawień, które są wyświetlane jako "punkt niestandardowe ustawienia", oznacza to, jak pole wyboru. Użyjesz tych pól wyboru do wybierz kategorie, aby zachować w pliku .vsettings. Kreator umożliwia .vsettings plikowi nazwę i wprowadź jego ścieżkę.  
  
> [!NOTE]
>  Ustawienia są zapisywane lub przywrócone jako kategorii i nazwy poszczególnych ustawień nie są wyświetlane w kreatorze.  
  
 Środowiska pakietu zarządzanego (MPF) obsługuje tworzenie kategorii ustawień z co najmniej dodatkowego kodu.  
  
-   Tworzenie pakietu VSPackage zapewnić kontener dla kategorii, podklasy <xref:Microsoft.VisualStudio.Shell.Package> klasy.  
  
-   Tworzenie kategorii, sama przez wywodzić ją z <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy.  
  
-   Łączenie dwóch z <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="support-for-settings-categories"></a>Obsługa ustawień kategorii  
 <xref:Microsoft.VisualStudio.Shell.Package> Klasy zapewnia obsługę tworzenia kategorii. <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasa implementuje kategorii. Domyślna implementacja klasy <xref:Microsoft.VisualStudio.Shell.DialogPage> oferuje jego właściwości publiczne do użytkownika jako kategorii. Aby uzyskać więcej informacji, zobacz [Tworzenie kategorii ustawień](../extensibility/creating-a-settings-category.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasy implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager>, co umożliwia utrzymywanie strony opcji i ustawień użytkownika. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> i <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> metody utrwalanie ustawień do .vssettings pliku, który [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>, odpowiednio. <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> Metoda resetuje ustawienia do wartości domyślnych.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasa zawiera implementację <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> metodę, która odczytuje pary nazwa wartość z pliku xml źródła danych i używa odbicia do odnajdywania właściwości publiczne w <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy pochodnej. Właściwości, które mają nazwy, które odpowiadają pary nazwa wartość są podane odpowiednie wartości.  
  
 Domyślna implementacja klasy <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> używa odbicia do odnajdywania właściwości publiczne w <xref:Microsoft.VisualStudio.Shell.DialogPage> klasę pochodną i zapisuje nazw właściwości i wartości do korzystania ze źródła XML jako pary nazwa wartość.  
  
### <a name="settings-category-registry-path"></a>Ścieżka rejestru kategorii ustawień  
 Ścieżka rejestru kategorii ustawień jest określana przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, wyraz, ustawienia użytkownika, kategoria ustawienia i nazwę punktu ustawienia niestandardowe. Nazwy kategorii ustawień i punktu ustawienia niestandardowe są przyłączone do i oddzielone znakiem podkreślenia w celu utworzenia canonical, niezlokalizowana Nazwa wyświetlana w rejestrze. Na przykład jeśli kategoria ustawień jest "Mój Category", "Moje ustawienia nazwy" i ApplicationRegistryRoot HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp punktu niestandardowe ustawienia, a następnie kategorii ustawień ma klucz rejestru, HKEY_LOCAL_ Ustawienia Category_My MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My.  
  
> [!NOTE]
>  Nazwa kanoniczna nie są wyświetlane w interfejsie użytkownika (UI). Służy do kojarzenia można odczytać nazwy z kategorii ustawienia, podobnie jak identyfikator programowy (ProgID).  
  
### <a name="settings-category-attribute"></a>Atrybutu kategorii ustawień  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Określa mapowanie kategorii do punktów ustawienia niestandardowe w **Kreatora importowania i eksportowania ustawień** kategorii można skojarzyć z pakietu VSPackage, który ją obsługuje. Rozważmy następujący fragment kodu:  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 Identyfikator zasobu 106 mapuje "Moje Category", 107 "Moje ustawienia" i 108 "Różne opcje". To oświadcza, że `MyPackage` zapewnia kategorii Moje ustawienia Category_My. Kategoria jest dostarczany przez `OptionsPageGeneral` klasy, która musi implementować <xref:Microsoft.VisualStudio.Shell.IProfileManager>. Ustawienia w tej kategorii są publicznymi właściwościami `OptionsPageGeneral` klasy.  
  
 W **Kreatora importowania i eksportowania ustawień**, punkt ustawienia ma nazwę Moje ustawienia. Po wybraniu w punkcie ustawienia, opis, **różne opcje**, zostanie wyświetlony. Ustawienia punktu nazwę i opis są pobierane z zasobów zlokalizowanych ciągów.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie strony opcji](../extensibility/creating-an-options-page.md)   
 [Przykłady VSSDK](../misc/vssdk-samples.md)   
 [Stan pakietu VSPackage](../misc/vspackage-state.md)   
 [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)