---
title: Używanie czcionek i kolorów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96abe68838d028c5de9d6d9418e94ba5b46c0f76
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693415"
---
# <a name="using-fonts-and-colors"></a>Używanie czcionek i kolorów
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Zapewnia obsługę wyświetlania tekstu przy użyciu czcionek i kolorów.

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie kolorów i czcionek](../extensibility/font-and-color-overview.md) w tym artykule omówiono ustawienia czcionek i kolorów tekstu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). Ponadto wprowadza pojęcia kategorii i wyświetlenie elementów i w tym artykule opisano, jak pakietów VSPackage i podstawowy edytor za pomocą atrybutów tekstu.

- [Pobieranie czcionek i kolorów informacji Kolorowanie tekstu](../extensibility/getting-font-and-color-information-for-text-colorization.md) zawiera wskazówki dotyczące implementowania Kolorowanie tekstu w pakietach VSPackage, zarządzać **kategorie** innych niż **edytora tekstów**.

- [Uzyskiwanie dostępu do przechowywanych czcionkę i kolor ustawienia](../extensibility/accessing-stored-font-and-color-settings.md) Explains jak bieżące ustawienia czcionek i kolorów, mogą być przechowywane, pobieranie i stosowanie.

- [Implementowanie niestandardowych kategorii i wyświetlanie elementów](../extensibility/implementing-custom-categories-and-display-items.md) opisano podstawowe kroki, według których okna można tworzyć i używać własnego programu **wyświetlania elementów** i **kategorie** do obsługi wyświetlania tekstu.

 Takie podejście wymaga pakietu VSPackage do zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu i interfejsy powiązane.

- [Instrukcje: Dostęp do wbudowanych czcionek i schemat kolorów](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md) omawia jak zdefiniować i zarejestrować kategorii przy użyciu wbudowanych czcionek i kolorów i zainicjować użycie dostarczane przez system czcionek i kolorów.

## <a name="reference"></a>Tematy pomocy
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Udostępnia wystąpienia `IVsFontAndColorDefaults` lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejs, który odnosi się do określonego elementu na liście **Pokaż ustawienia dla** listy w **czcionki i kolory** strony **Opcje** okno dialogowe.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Włącza VSPackage do obsługi środowiska IDE **czcionki i kolory** strony, definiując domyślny czcionki i kolory w oknie lub składnik interfejsu użytkownika.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Udostępnia mechanizm, za pomocą którego pakietu VSPackage, który zapewnia obsługę czcionek i kolorów można określić grupę wyświetlanego elementu — bardzo kategorię, która reprezentuje sumę dwóch lub więcej kategorii.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Umożliwia VSPackage można pobrać danych czcionek i kolorów lub zapisać go w rejestrze.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Powiadamia pakietów VSPackage przy użyciu czcionek i kolorów informacje o zmianach wprowadzonych w ustawieniach czcionek i kolorów.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities> Udostępnia narzędzia do pracy z danych wejściowych i wyjściowych, który jest używany przez metody [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **czcionek i kolorów** mechanizm.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Kontroluje, buforowanie ustawienia czcionek i kolorów.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md) w tym artykule omówiono, jak pakietów VSPackage języka usługi służy do dostosowywania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytora.

- [Kolorowanie składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md) Descries sposób, w jaki [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor używa usług językowych do zaimplementowania kolorowanie składni.

- [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md) wyjaśnia, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usługi, aby tworzyć elementy interfejsu użytkownika, które pasują reszty [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].