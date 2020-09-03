---
title: Obsługa kategorii ustawień | Microsoft Docs
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
ms.openlocfilehash: 15a3896f8a2010a063393d3a11c1ed3453a008d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689098"
---
# <a name="support-for-settings-categories"></a>Obsługa kategorii ustawień
Kategoria ustawień składa się z grupy opcji, które dostosowują zintegrowane środowisko programistyczne (IDE). Na przykład ustawienia mogą kontrolować układ [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okien i zawartość menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 W menu **Narzędzia** kliknij pozycję **Importuj i Eksportuj ustawienia** , aby uruchomić **Kreatora importowania i eksportowania ustawień**. Kreator oferuje trzy opcje: eksport, import lub Resetowanie ustawień. Po wybraniu opcji Eksportuj na przykład zostanie otwarta strona **Wybieranie ustawień do eksportowania** w kreatorze.  
  
 Kontrolka drzewa w okienku nawigacji na tej stronie zawiera listę kategorii. Kategoria jest grupą powiązanych ustawień, które są wyświetlane jako "punkt ustawień niestandardowych", czyli jako pole wyboru. Te pola wyboru służą do wybierania kategorii, które mają być utrwalane w pliku. vsettings. Kreator pozwala nazwać plik. vsettings i określić jego ścieżkę.  
  
> [!NOTE]
> Ustawienia są zapisywane lub przywracane jako kategoria, a indywidualne nazwy ustawień nie są wyświetlane w kreatorze.  
  
 Struktura pakietu zarządzanego (MPF) obsługuje tworzenie kategorii ustawień z co najmniej dodatkowym kodem.  
  
- Tworzysz pakietu VSPackage, aby dostarczyć kontener dla kategorii przez podklasy <xref:Microsoft.VisualStudio.Shell.Package> klasy.  
  
- Samą kategorię można utworzyć, wyprowadzając ją z <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy.  
  
- Dwa z nich łączą się <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .  
  
## <a name="support-for-settings-categories"></a>Obsługa kategorii ustawień  
 <xref:Microsoft.VisualStudio.Shell.Package>Klasa zapewnia obsługę tworzenia kategorii. <xref:Microsoft.VisualStudio.Shell.DialogPage>Klasa implementuje kategorię. Domyślna implementacja programu <xref:Microsoft.VisualStudio.Shell.DialogPage> oferuje jego właściwości publiczne użytkownikowi jako kategorię. Aby uzyskać więcej informacji, zobacz [Tworzenie kategorii ustawień](../extensibility/creating-a-settings-category.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>Klasa implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager> , która zapewnia trwałość dla obu stron opcji i ustawień użytkownika. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>Metody i <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> zachowują ustawienia w pliku VSSETTINGS, który [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> odpowiednio lub. <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A>Metoda resetuje ustawienia do wartości domyślnych.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>Klasa zawiera implementację <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> metody, która odczytuje pary nazwa-wartość ze źródła danych XML, i używa odbicia do odnajdywania właściwości publicznych w <xref:Microsoft.VisualStudio.Shell.DialogPage> klasie pochodnej. Właściwości, które mają nazwy, które pasują do par nazwa-wartość, otrzymują odpowiednie wartości.  
  
 Domyślna implementacja programu <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> używa odbicia do odnajdywania właściwości publicznych w <xref:Microsoft.VisualStudio.Shell.DialogPage> klasie pochodnej i zapisuje nazwy właściwości i wartości do źródła danych XML jako pary nazwa-wartość.  
  
### <a name="settings-category-registry-path"></a>Ścieżka rejestru kategorii ustawień  
 Ścieżka rejestru kategorii ustawień jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , słowo, UserSettings, kategorię ustawień i nazwę punktu ustawień niestandardowych. Nazwy kategorii ustawień i punktu ustawień niestandardowych są przyłączone i oddzielane znakiem podkreślenia w celu utworzenia kanonicznej, niezlokalizowanej nazwy, która pojawia się w rejestrze. Na przykład jeśli Kategoria ustawienia to "Moja Kategoria", nazwa punktu ustawień niestandardowych "Moje ustawienia" i ApplicationRegistryRoot HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, a następnie Kategoria ustawienia ma klucz rejestru HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My ustawienia.  
  
> [!NOTE]
> Nazwa kanoniczna nie jest wyświetlana w interfejsie użytkownika. Służy do kojarzenia nazwy z możliwością odczytu z kategorią ustawień, podobnie jak identyfikator programowy (ProgID).  
  
### <a name="settings-category-attribute"></a>Atrybut kategorii ustawień  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>Określa mapowanie kategorii do punktów ustawień niestandardowych w **Kreatorze importu i eksportu ustawień** przez skojarzenie kategorii z pakietu vspackageą, która go udostępnia. Rozważmy następujący fragment kodu:  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 Identyfikator zasobu 106 mapuje na "My Category", 107 do "My Settings" i 108 do "różnych opcji". Deklaruje, że `MyPackage` zawiera ustawienia Kategoria, moje Category_My. Kategoria jest dostarczana przez `OptionsPageGeneral` klasę, która musi implementować <xref:Microsoft.VisualStudio.Shell.IProfileManager> . Ustawienia w tej kategorii są publicznymi właściwościami `OptionsPageGeneral` klasy.  
  
 W **Kreatorze importowania i eksportowania ustawień**punkt ustawień ma nazwę, moje ustawienia. Po wybraniu punktu ustawień zostanie wyświetlony opis, **różne opcje**. Nazwa i opis punktu ustawień są pobierane z zlokalizowanych zasobów ciągu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie strony opcji](../extensibility/creating-an-options-page.md)   
 [Przykłady VSSDK](../misc/vssdk-samples.md)   
 [Stan pakietu VSPackage](../misc/vspackage-state.md)   
 [Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)