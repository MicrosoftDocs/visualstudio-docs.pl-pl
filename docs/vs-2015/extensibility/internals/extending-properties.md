---
title: Rozszerzanie właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690994"
---
# <a name="extending-properties"></a>Rozszerzanie właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Właściwości** to uniwersalna przeglądarka właściwości dla składników com i com+, która obsługuje wszystkie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] produkty. Okno **Właściwości** działa z `ITypeInfo` informacjami o typie i metadanych modelu COM+, aby wyświetlić właściwości czasu projektowania aktualnie zaznaczonego obiektu w dowolnym innym oknie w zintegrowanym środowisku programistycznym (IDE).  
  
 Okno **Właściwości** , które można otworzyć przez naciśnięcie klawisza F4 na klawiaturze lub wybranie **okna właściwości** w menu **Widok** , służy do wyświetlania i edytowania właściwości niezależnych od konfiguracji, czasu projektowania i zdarzeń wybranych obiektów. Właściwości zależne od konfiguracji, skojarzone z rozwiązaniami i projektami, są wyświetlane na [stronach właściwości](../../extensibility/internals/property-pages.md). Aby uzyskać więcej informacji, zobacz [NIB: właściwości projektu](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)i [NIB: Zarządzanie elementami w projektach](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Omówienie okna właściwości](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Okno właściwości  
  
 Ta sekcja zawiera szczegółowe informacje dotyczące poszczególnych obszarów okna **Właściwości** oraz interfejsów, które należy zaimplementować, i wywoływać w celu wypełnienia okna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie okna właściwości](../../extensibility/internals/properties-window-overview.md)  
 Wyjaśnia przeznaczenie okna **Właściwości** względem okna narzędzi i okna dokumentu.  
  
 [Szablon zasad i okno właściwości](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 W tym artykule omówiono sposób, w jaki projekt jest zawarty w projekcie szablonu przedsiębiorstwa, oraz sposób, w jaki projekt szablonu przedsiębiorstwa może wymusić zasady.  
  
 [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Wyjaśnia podstawę wyboru, która określa, jakie informacje są wyświetlane w oknie **Właściwości** .  
  
 [Lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md)  
 Opisuje przeznaczenie listy obiektów okna **Właściwości** , opisując, w jaki sposób, gdy inny obiekt z tej listy wyzwala wywołanie, środowisko jest poinformowane o tym, że został wybrany nowy obiekt.  
  
 [Przyciski okna właściwości](../../extensibility/internals/properties-window-buttons.md)  
 Wyjaśnia przeznaczenie czterech domyślnych przycisków wyświetlanych na pasku narzędzi okna **Właściwości** .  
  
 [Siatka wyświetlania właściwości](../../extensibility/internals/properties-display-grid.md)  
 Wyjaśnia, gdzie nazwy właściwości i pola wartości właściwości znajdują się w siatce.  
  
 [Ogłoszenie śledzenia wyboru okna właściwości](../../misc/announcing-property-window-selection-tracking.md)  
 Opisuje śledzenie wyboru dla okna **Właściwości** .  
  
 [Ukrywanie właściwości, które mają właściwości podrzędne](../../misc/hiding-properties-that-have-child-properties.md)  
 Wyjaśnia, jak ukryć właściwości, które mają właściwości podrzędne przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> interfejsu.  
  
 [Udostępnianie okna właściwości niestandardowych](../../misc/providing-a-custom-properties-window.md)  
 Szczegółowe instrukcje dotyczące udostępniania własnej przeglądarki właściwości.  
  
 [Pobieranie opisów pól z okna właściwości](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Wyjaśnia, gdzie znaleźć obszar opisu, który wyświetla informacje powiązane z wybranym polem właściwości.  
  
 [Aktualizowanie wartości właściwości w oknie właściwości](../../misc/updating-property-values-in-the-properties-window.md)  
 Zawiera instrukcje krok po kroku, które pokazują dwa sposoby synchronizowania okna **Właściwości** ze zmianami wartości właściwości.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Omawia projekty jako bloki konstrukcyjne [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska IDE.  
  
 [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)  
 Opisuje, w jaki sposób można używać [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] platformy do ciągłego testowania i debugowania aplikacji podczas ich kompilowania.  
  
 [Właściwości dokumentu HTML, okno właściwości](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Zawiera instrukcje dotyczące edytowania dokumentu HTML bezpośrednio z okno Właściwości i zawiera tabelę zawierającą szczegółowe informacje o polach w dokumencie HTML w okno Właściwości.  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Opisuje `IDispatch` interfejs, który został pierwotnie zaprojektowany do obsługi automatyzacji, zapewniając mechanizm z późnym wiązaniem do uzyskiwania dostępu i pobierania informacji o metodach i właściwościach obiektu.  
  
 [NIB: wprowadzenie do właściwości dynamicznych (Visual Studio)](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Zawiera omówienie właściwości dynamicznych, które umożliwiają skonfigurowanie aplikacji w taki sposób, aby wartości właściwości były przechowywane w zewnętrznym pliku konfiguracji, a nie w skompilowanym kodzie aplikacji.  
  
 [NIB: projekty jako kontenery](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Opisuje rolę projektu jako kontener w rozwiązaniu, aby logicznie zarządzać, kompilować i debugować elementy wchodzące w skład aplikacji.  
  
 [NIB: właściwości projektu](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Opisuje, w jaki sposób projekt zarządza ustawieniami, które umożliwiają kontrolowanie właściwości, które mają zastosowanie do całego projektu, a także właściwości, które są ograniczone do niektórych konfiguracji kompilacji projektu.  
  
 [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)  
 Wyjaśnia, jak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] efektywnie zarządza elementami, takimi jak odwołania, połączenia danych, foldery i pliki, które są wymagane przez nakład pracy deweloperskiej za pomocą rozwiązań i projektów.  
  
 [Rozszerzanie innych części programu Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Wyjaśnia, jak używać [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usług do tworzenia elementów interfejsu użytkownika, które pasują do pozostałej części [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
