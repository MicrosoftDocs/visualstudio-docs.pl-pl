---
title: Rozszerzanie właściwości | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84fef8d0f63f76c7810c94ade2e1eb58e55b94cd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602978"
---
# <a name="extend-properties"></a>Rozszerzanie właściwości
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Właściwości** okna jest przeglądarkę właściwości uniwersalnych dla składników COM i COM + i obsługuje wszystkie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produktów. **Właściwości** okna współpracuje z `ITypeInfo` typu informacji i metadanych modelu COM +, aby wyświetlić listę właściwości czasu projektowania dla aktualnie wybranego obiektu w innym oknie zintegrowanego środowiska programistycznego (IDE).

 **Właściwości** okno, które można otworzyć, naciskając klawisz **F4** na klawiaturze lub wybierając **okno właściwości** na **widoku** menu Służy do wyświetlania i edytowania właściwości niezależne od konfiguracji, w czasie projektowania oraz zdarzeń zaznaczonych obiektów. Właściwości zależne od konfiguracji, skojarzone z rozwiązaniami i projektami, są wyświetlane na [stron właściwości](../../extensibility/internals/property-pages.md). Aby uzyskać więcej informacji [Zarządzaj opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).

 ![Omówienie okna właściwości](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") okno właściwości

 Ta sekcja zawiera szczegółowe informacje, które odnoszą się do poszczególnych obszarów **właściwości** okna i interfejsy, które należy zaimplementować i wywołania do wypełnienia okna.

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie okna właściwości](../../extensibility/internals/properties-window-overview.md)

 Zawiera wyjaśnienie przeznaczenia **właściwości** okna względem okna narzędzi i okna dokumentu.

- [Szablon zasad i okno właściwości](../../extensibility/internals/template-policy-and-the-properties-window.md)

 W tym artykule omówiono, jak projekt jest zawarta w szablonie projektu w przedsiębiorstwie i jak ten szablon projektu przedsiębiorstwa mogą wymusić zasady.

- [Właściwości pola i interfejsy okna](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Wyjaśnia podstawę do wyboru, która określa, jakie informacje są wyświetlane w **właściwości** okna.

- [Lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md)

 Opisuje przeznaczenie **właściwości** lista obiektów okna, opisujące, jak to zrobić, gdy inny obiekt z tej listy wyzwala wywołanie, środowisko jest informowany wybrano nowego obiektu.

- [Przyciski okna właściwości](../../extensibility/internals/properties-window-buttons.md)

 Zawiera wyjaśnienie przeznaczenia cztery domyślne przyciski wyświetlane na **właściwości** pasek narzędzi okna.

- [Siatka wyświetlania właściwości](../../extensibility/internals/properties-display-grid.md)

 W tym artykule wyjaśniono, w którym nazw właściwości i pola wartości właściwości znajdują się w siatce.

## <a name="related-sections"></a>Sekcje pokrewne
- [Typy projektów](../../extensibility/internals/project-types.md)

 W tym artykule omówiono projektów jako bloki konstrukcyjne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Kompilowanie i tworzenie kompilacji](../../ide/compiling-and-building-in-visual-studio.md)

 W tym artykule opisano, jak można użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] platformy ciągłe testowanie i debugowanie aplikacji podczas ich tworzenia.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 W tym artykule opisano `IDispatch` interfejs, który pierwotnie opracowano do obsługi automatyzacji, zapewnienie mechanizmu przekazującego z późnym wiązaniem dostępu i pobieranie informacji na temat metod i właściwości obiektu.

- [Zarządzanie ustawieniami aplikacji (.NET)](../../ide/managing-application-settings-dotnet.md)

 Zawiera omówienie ustawienia aplikacji, które pozwalają skonfigurować aplikację tak, aby wartości właściwości są przechowywane w pliku konfiguracji zewnętrznego zamiast skompilowany kod aplikacji.

- [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)

 Wyjaśnia, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] efektywnie zarządza elementy, takie jak odwołania, połączenia danych, folderów i plików, które są wymagane przez nakładów pracy programowania za pomocą rozwiązań i projektów.

- [Rozszerzanie innych części programu Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Opis sposobu użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usługi, aby tworzyć elementy interfejsu użytkownika, które pasują reszty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].