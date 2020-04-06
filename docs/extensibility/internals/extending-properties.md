---
title: Właściwości rozszerzające | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708418"
---
# <a name="extend-properties"></a>Rozszerzanie właściwości
Okno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Właściwości** jest uniwersalną przeglądarką właściwości dla składników [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] COM i COM+ i obsługuje wszystkie produkty. Okno **Właściwości** współpracuje `ITypeInfo` z informacjami o typie i metadanymi COM+, aby wyświetlić listę właściwości czasu projektowania aktualnie wybranego obiektu w dowolnym innym oknie w zintegrowanym środowisku programistycznym (IDE).

 Okno **Właściwości,** które można otworzyć, naciskając **klawisz F4** na klawiaturze lub wybierając **okno Właściwości** w menu **Widok,** służy do wyświetlania i edytowania właściwości i zdarzeń wybranych obiektów niezależnych od konfiguracji, w czasie projektowania i zdarzeń. Właściwości zależne od konfiguracji, skojarzone z rozwiązaniami i projektami, są wyświetlane na [stronach właściwości](../../extensibility/internals/property-pages.md). Aby uzyskać więcej informacji, [zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).

 ![Omówienie okna właściwości](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Okno Właściwości

 Ta sekcja zawiera szczegółowe informacje, które odnoszą się do poszczególnych obszarów właściwości okna i **interfejsów,** które należy zaimplementować i wywołać, aby wypełnić okno.

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie okna właściwości](../../extensibility/internals/properties-window-overview.md)

 W tym artykule opisano przeznaczenie okna **Właściwości** względem okna narzędzia i okna dokumentu.

- [Zasady szablonu i okno Właściwości](../../extensibility/internals/template-policy-and-the-properties-window.md)

 W tym artykule omówiono sposób, w jaki projekt jest zawarty w projekcie szablonu przedsięwzięcia i jak ten projekt szablonu przedsięwzięcia może wymuszać zasady.

- [Właściwości pola okienne i interfejsy](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 W tym artykule wyjaśniono podstawę wyboru, która określa, jakie informacje są wyświetlane w oknie **Właściwości.**

- [Lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md)

 Opisuje cel listy obiektów okna **Właściwości,** opisując, jak, gdy inny obiekt z tej listy wyzwala wywołanie, środowisko jest informowany, że nowy obiekt został wybrany.

- [Właściwości przyciski okna](../../extensibility/internals/properties-window-buttons.md)

 W tym artykule opisano przeznaczenie czterech przycisków **domyślnych wyświetlanych** na pasku narzędzi okna Właściwości.

- [Właściwości wyświetlają siatkę](../../extensibility/internals/properties-display-grid.md)

 W tym artykule wyjaśniono, gdzie znajdują się nazwy właściwości i wartości właściwości w siatce.

## <a name="related-sections"></a>Powiązane sekcje
- [Typy projektów](../../extensibility/internals/project-types.md)

 W tym artykule omówiono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty jako elementy składowe IDE.

- [Kompilowanie i tworzenie kompilacji](../../ide/compiling-and-building-in-visual-studio.md)

 W tym artykule [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opisano, jak można używać platformy do ciągłego testowania i debugowania aplikacji podczas ich tworzenia.

- [Idispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Opisuje `IDispatch` interfejs, który został zaprojektowany po raz pierwszy do obsługi automatyzacji, zapewniając późno powiązany mechanizm dostępu i pobierania informacji o metodach i właściwościach obiektu.

- [Zarządzanie ustawieniami aplikacji (.NET)](../../ide/managing-application-settings-dotnet.md)

 Zawiera omówienie ustawień aplikacji, które umożliwiają skonfigurowanie aplikacji tak, aby wartości właściwości były przechowywane w zewnętrznym pliku konfiguracyjnym zamiast skompilowanego kodu aplikacji.

- [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)

 W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tym artykule wyjaśniono, jak skutecznie zarządza elementami, takimi jak odwołania, połączenia danych, foldery i pliki, które są wymagane przez wysiłek związany z programem za pomocą rozwiązań i projektów.

- [Rozszerzanie innych części programu Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 W tym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] artykule wyjaśniono, jak używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usług do tworzenia elementów interfejsu użytkownika, które pasują do reszty .
