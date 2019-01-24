---
title: Rozszerzanie właściwości | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 59afc6a95e327460602ece8db58f075b483d0e09
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776431"
---
# <a name="extending-properties"></a>Rozszerzanie właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Właściwości** okna jest przeglądarkę właściwości uniwersalnych dla składników COM i COM + i obsługuje wszystkie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] produktów. **Właściwości** okna współpracuje z `ITypeInfo` typu informacji i metadanych modelu COM +, aby wyświetlić listę właściwości czasu projektowania dla aktualnie wybranego obiektu w innym oknie zintegrowanego środowiska programistycznego (IDE).  
  
 **Właściwości** okno, które można otworzyć, naciskając klawisz F4 na klawiaturze lub wybierając **okno właściwości** na **widoku** menu służy do wyświetlania i edytowania niezależne od konfiguracji, w czasie projektowania, właściwości i zdarzeń zaznaczonych obiektów. Właściwości zależne od konfiguracji, skojarzone z rozwiązaniami i projektami, są wyświetlane na [stron właściwości](../../extensibility/internals/property-pages.md). Aby uzyskać więcej informacji, zobacz [właściwości NIB: projektu](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [zarządzanie opcje konfiguracji](../../extensibility/internals/managing-configuration-options.md), i [zarządzania NIB: element w projektach](http://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Omówienie okna właściwości](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Okno właściwości  
  
 Ta sekcja zawiera szczegółowe informacje, które odnoszą się do poszczególnych obszarów **właściwości** okna i interfejsy, które należy zaimplementować i wywołania do wypełnienia okna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie okna właściwości](../../extensibility/internals/properties-window-overview.md)  
 Zawiera wyjaśnienie przeznaczenia **właściwości** okna względem okna narzędzi i okna dokumentu.  
  
 [Szablon zasad i okno właściwości](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 W tym artykule omówiono, jak projekt jest zawarta w szablonie projektu w przedsiębiorstwie i jak ten szablon projektu przedsiębiorstwa mogą wymusić zasady.  
  
 [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Wyjaśnia podstawę do wyboru, która określa, jakie informacje są wyświetlane w **właściwości** okna.  
  
 [Lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md)  
 Opisuje przeznaczenie **właściwości** lista obiektów okna, opisujące, jak to zrobić, gdy inny obiekt z tej listy wyzwala wywołanie, środowisko jest informowany wybrano nowego obiektu.  
  
 [Przyciski okna właściwości](../../extensibility/internals/properties-window-buttons.md)  
 Zawiera wyjaśnienie przeznaczenia cztery domyślne przyciski wyświetlane na **właściwości** pasek narzędzi okna.  
  
 [Siatka wyświetlania właściwości](../../extensibility/internals/properties-display-grid.md)  
 W tym artykule wyjaśniono, w którym nazw właściwości i pola wartości właściwości znajdują się w siatce.  
  
 [Ogłoszenie wybór okna właściwości śledzenia](../../misc/announcing-property-window-selection-tracking.md)  
 W tym artykule opisano wybór śledzenie **właściwości** okna.  
  
 [Ukrywanie właściwości, które mają właściwości podrzędnej](../../misc/hiding-properties-that-have-child-properties.md)  
 Wyjaśnia, jak Ukryj właściwości, które mają właściwości podrzędnej implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> interfejsu.  
  
 [Zapewnianie okno właściwości niestandardowe](../../misc/providing-a-custom-properties-window.md)  
 Szczegółowe kroki zapewniające przeglądarkę właściwości.  
  
 [Wprowadzenie opisy pól z okna właściwości](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Wyjaśnia, gdzie można znaleźć obszaru Opis, który wyświetla informacje związane z pól wybranych właściwości.  
  
 [Aktualizowanie wartości właściwości w oknie dialogowym właściwości](../../misc/updating-property-values-in-the-properties-window.md)  
 Zawiera instrukcje krok po kroku, w których wyświetlane są dwa sposoby, aby zachować **właściwości** okna synchronizowane z zmiany wartości właściwości.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 W tym artykule omówiono projektów jako bloki konstrukcyjne [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)  
 W tym artykule opisano, jak można użyć [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] platformy ciągłe testowanie i debugowanie aplikacji podczas ich tworzenia.  
  
 [Właściwości dokumentu HTML, okno właściwości](http://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Zawiera instrukcje dotyczące edytowania dokumentu HTML bezpośrednio w oknie właściwości i zawiera tabela przedstawiająca szczegółowo pola w dokumencie HTML w oknie dialogowym właściwości.  
  
 [IDispatch](http://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 W tym artykule opisano `IDispatch` interfejs, który pierwotnie opracowano do obsługi automatyzacji, zapewnienie mechanizmu przekazującego z późnym wiązaniem dostępu i pobieranie informacji na temat metod i właściwości obiektu.  
  
 [NIB: Wprowadzenie do właściwości dynamicznych (Visual Studio)](http://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Zawiera omówienie właściwości dynamicznych, które pozwalają skonfigurować aplikację tak, aby wartości właściwości są przechowywane w pliku konfiguracji zewnętrznego zamiast skompilowany kod aplikacji.  
  
 [NIB: projekty, jako kontenery](http://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 W tym artykule opisano rolę projektu jako kontener w rozwiązaniu do logicznie zarządzania, tworzenie i debugowanie elementy, które składają się na aplikację.  
  
 [NIB:Project Properties](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 W tym artykule opisano, jak projekt zarządza ustawienia, które umożliwiają właściwości kontrolki, które są stosowane do całego projektu, a także właściwości, które są ograniczone do niektórych konfiguracje kompilacji projektu.  
  
 [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)  
 Wyjaśnia, jak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] efektywnie zarządza elementy, takie jak odwołania, połączenia danych, folderów i plików, które są wymagane przez nakładów pracy programowania za pomocą rozwiązań i projektów.  
  
 [Rozszerzanie innych części programu Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Opis sposobu użycia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usługi, aby tworzyć elementy interfejsu użytkownika, które pasują reszty [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].
