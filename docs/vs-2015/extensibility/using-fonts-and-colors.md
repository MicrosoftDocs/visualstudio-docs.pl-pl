---
title: Używanie czcionek i kolorów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177222"
---
# <a name="using-fonts-and-colors"></a>Korzystanie z czcionek i kolorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Zapewnia obsługę używania czcionek i kolorów do wyświetlania tekstu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie czcionek i kolorów](../extensibility/font-and-color-overview.md)  
 Omawia ustawienia czcionek i kolorów tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE). Wprowadza również pojęcia dotyczące kategorii i elementów wyświetlanych oraz opisuje, jak pakietów VSPackage i podstawowy edytor używają atrybutów tekstu.  
  
 [Uzyskiwanie informacji o czcionkach i kolorach na potrzeby kolorowania tekstu](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Zawiera wytyczne dotyczące implementowania kolorowania tekstu w pakietów VSPackage, który zarządza **kategoriami** innymi niż **Edytor tekstu**.  
  
 [Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md)  
 Wyjaśnia, w jaki sposób bieżące ustawienia czcionek i kolorów mogą być przechowywane, pobierane i stosowane.  
  
 [Implementowanie kategorii niestandardowych i elementów wyświetlanych](../extensibility/implementing-custom-categories-and-display-items.md)  
 W tym artykule opisano podstawowe kroki, za pomocą których okno może tworzyć własne **elementy** i **Kategorie** i korzystać z nich w celu obsługi wyświetlania tekstu.  
  
 To podejście wymaga pakietu VSPackage, aby zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejs i powiązane interfejsy.  
  
 [Instrukcje: uzyskiwanie dostępu do wbudowanych czcionek i schematu kolorów](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 W tym artykule omówiono sposób definiowania i rejestrowania kategorii przy użyciu wbudowanych czcionek i kolorów oraz inicjowania używania czcionek i kolorów dostarczonych przez system.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Zapewnia wystąpienie `IVsFontAndColorDefaults` lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejs, który odnosi się do określonego elementu wymienionego na liście **Pokaż ustawienia dla** listy na stronie **czcionki i kolory** okna dialogowego **Opcje** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Włącza pakietu VSPackage do obsługi **czcionek i kolorów** IDE, definiując domyślne czcionki i kolory dla składnika okna lub interfejsu użytkownika.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Zapewnia mechanizm, za pomocą którego pakietu VSPackage, który zapewnia obsługę czcionek i kolorów, może określać grupę elementów wyświetlania — nadrzędną kategorię, która reprezentuje Unię dwóch lub więcej kategorii.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Umożliwia pakietu VSPackage pobieranie czcionek i danych kolorów lub zapisywanie ich w rejestrze.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Powiadamia pakietów VSPackage, które używają informacji o czcionkach i kolorach o zmianach w ustawieniach czcionek i kolorów.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Oferuje narzędzia do pracy z danymi wejściowymi i wyjściowymi, które są używane przez metody stosowane w metodach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **czcionki i mechanizmu koloru** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Steruje buforowaniem ustawień czcionek i kolorów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)  
 W tym artykule omówiono sposób, w jaki pakietów VSPackage może używać usług języka do dostosowywania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora.  
  
 [Kolorowania składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries, jak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytor używa usług języka do implementowania kolorowania składni.  
  
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Wyjaśnia, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usług do tworzenia elementów interfejsu użytkownika, które pasują do pozostałej części [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .
