---
title: Używanie czcionek i kolorów | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177222"
---
# <a name="using-fonts-and-colors"></a>Korzystanie z czcionek i kolorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Zapewnia obsługę wyświetlania tekstu przy użyciu czcionek i kolorów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie czcionek i kolorów](../extensibility/font-and-color-overview.md)  
 W tym artykule omówiono ustawienia czcionek i kolorów tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE). Ponadto wprowadza pojęcia kategorii i wyświetlenie elementów i w tym artykule opisano, jak pakietów VSPackage i podstawowy edytor za pomocą atrybutów tekstu.  
  
 [Uzyskiwanie informacji o czcionkach i kolorach na potrzeby kolorowania tekstu](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Zawiera wskazówki dotyczące implementowania Kolorowanie tekstu w pakietach VSPackage, zarządzać **kategorie** innych niż **edytora tekstów**.  
  
 [Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md)  
 Wyjaśnia, jak bieżący czcionek i kolorów ustawień mogą być przechowywane pobierane i stosowane.  
  
 [Implementowanie kategorii niestandardowych i elementów wyświetlanych](../extensibility/implementing-custom-categories-and-display-items.md)  
 W tym artykule opisano podstawowe kroki, według których okna można tworzyć i używać własnego programu **wyświetlania elementów** i **kategorie** do obsługi wyświetlania tekstu.  
  
 Takie podejście wymaga pakietu VSPackage do zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu i interfejsy powiązane.  
  
 [Instrukcje: uzyskiwanie dostępu do wbudowanych czcionek i schematu kolorów](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 W tym artykule omówiono, jak zdefiniować i zarejestrować kategorii przy użyciu wbudowanych czcionek i kolorów i zainicjować użycie dostarczane przez system czcionek i kolorów.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Udostępnia wystąpienia `IVsFontAndColorDefaults` lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejs, który odnosi się do określonego elementu na liście **Pokaż ustawienia dla** listy w **czcionki i kolory** strony **Opcje** okno dialogowe.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Włącza VSPackage do obsługi środowiska IDE **czcionki i kolory** strony, definiując domyślny czcionki i kolory w oknie lub składnik interfejsu użytkownika.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Udostępnia mechanizm, za pomocą którego pakietu VSPackage, który zapewnia obsługę czcionek i kolorów można określić grupę wyświetlanego elementu — bardzo kategorię, która reprezentuje sumę dwóch lub więcej kategorii.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Umożliwia VSPackage można pobrać danych czcionek i kolorów lub zapisać go w rejestrze.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Powiadamia pakietów VSPackage przy użyciu czcionek i kolorów informacje o zmianach wprowadzonych w ustawieniach czcionek i kolorów.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Udostępnia narzędzia do pracy z danych wejściowych i wyjściowych, który jest używany przez metody [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **czcionek i kolorów** mechanizm.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Kontroluje, buforowanie ustawienia czcionek i kolorów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)  
 W tym artykule omówiono, jak pakietów VSPackage języka usługi służy do dostosowywania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora.  
  
 [Kolorowania składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries sposób, w jaki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytor używa usług językowych do zaimplementowania kolorowanie składni.  
  
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Opis sposobu użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usługi, aby tworzyć elementy interfejsu użytkownika, które pasują reszty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].
