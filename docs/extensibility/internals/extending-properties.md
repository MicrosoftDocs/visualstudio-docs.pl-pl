---
title: Rozszerzanie właściwości | Microsoft Docs
description: Dowiedz się więcej na temat interfejsów, które należy zaimplementować, i Wywołaj, aby rozwinąć listę właściwości w okno Właściwości programu Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 721f45ebe83e0edb7bf7a182ea71b2181593ad6e
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479541"
---
# <a name="extend-properties"></a>Rozwiń właściwości
Okno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Właściwości** to uniwersalna przeglądarka właściwości dla składników com i com+, która obsługuje wszystkie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produkty. Okno **Właściwości** działa z `ITypeInfo` informacjami o typie i metadanych modelu COM+, aby wyświetlić właściwości czasu projektowania aktualnie zaznaczonego obiektu w dowolnym innym oknie w zintegrowanym środowisku programistycznym (IDE).

 Okno **Właściwości** , które można otworzyć przez naciśnięcie klawisza **F4** na klawiaturze lub wybranie **okna właściwości** w menu **Widok** , służy do wyświetlania i edytowania właściwości niezależnych od konfiguracji, czasu projektowania i zdarzeń wybranych obiektów. Właściwości zależne od konfiguracji, skojarzone z rozwiązaniami i projektami, są wyświetlane na [stronach właściwości](../../extensibility/internals/property-pages.md). Aby uzyskać więcej informacji, [Zarządzaj opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).

 ![Przegląd okno właściwości](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") okno Właściwości

 Ta sekcja zawiera szczegółowe informacje dotyczące poszczególnych obszarów okna **Właściwości** oraz interfejsów, które należy zaimplementować, i wywoływać w celu wypełnienia okna.

## <a name="in-this-section"></a>W tej sekcji
- [Przegląd okno Właściwości](../../extensibility/internals/properties-window-overview.md)

 Wyjaśnia przeznaczenie okna **Właściwości** względem okna narzędzi i okna dokumentu.

- [Zasady dotyczące szablonów i okno Właściwości](../../extensibility/internals/template-policy-and-the-properties-window.md)

 W tym artykule omówiono sposób, w jaki projekt jest zawarty w projekcie szablonu przedsiębiorstwa, oraz sposób, w jaki projekt szablonu przedsiębiorstwa może wymusić zasady.

- [okno Właściwości pól i interfejsów](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Wyjaśnia podstawę wyboru, która określa, jakie informacje są wyświetlane w oknie **Właściwości** .

- [Lista obiektów okno Właściwości](../../extensibility/internals/properties-window-object-list.md)

 Opisuje przeznaczenie listy obiektów okna **Właściwości** , opisując, w jaki sposób, gdy inny obiekt z tej listy wyzwala wywołanie, środowisko jest poinformowane o tym, że został wybrany nowy obiekt.

- [Przyciski okno Właściwości](../../extensibility/internals/properties-window-buttons.md)

 Wyjaśnia przeznaczenie czterech domyślnych przycisków wyświetlanych na pasku narzędzi okna **Właściwości** .

- [Siatka wyświetlania właściwości](../../extensibility/internals/properties-display-grid.md)

 Wyjaśnia, gdzie nazwy właściwości i pola wartości właściwości znajdują się w siatce.

## <a name="related-sections"></a>Sekcje pokrewne
- [Typy projektów](../../extensibility/internals/project-types.md)

 Omawia projekty jako bloki konstrukcyjne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska IDE.

- [Kompilowanie i tworzenie kompilacji](../../ide/compiling-and-building-in-visual-studio.md)

 Opisuje, w jaki sposób można używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] platformy do ciągłego testowania i debugowania aplikacji podczas ich kompilowania.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Opisuje `IDispatch` interfejs, który został pierwotnie zaprojektowany do obsługi automatyzacji, zapewniając mechanizm z późnym wiązaniem do uzyskiwania dostępu i pobierania informacji o metodach i właściwościach obiektu.

- [Zarządzanie ustawieniami aplikacji (.NET)](../../ide/managing-application-settings-dotnet.md)

 Zawiera omówienie ustawień aplikacji, które umożliwiają skonfigurowanie aplikacji w taki sposób, aby wartości właściwości były przechowywane w zewnętrznym pliku konfiguracji, a nie w skompilowanym kodzie aplikacji.

- [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)

 Wyjaśnia, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] efektywnie zarządza elementami, takimi jak odwołania, połączenia danych, foldery i pliki, które są wymagane przez nakład pracy deweloperskiej za pomocą rozwiązań i projektów.

- [Rozszerzając inne części programu Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Wyjaśnia, jak używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usług do tworzenia elementów interfejsu użytkownika, które pasują do pozostałej części [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
