---
title: Hierarchie w programie Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708189"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchie w programie Visual Studio
Zintegrowane [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko programistyczne (IDE) wyświetla projekt jako *hierarchię.* W IDE hierarchii jest drzewo węzłów, gdzie każdy węzeł ma zestaw skojarzonych właściwości. *Hierarchia projektu* to kontener, w który znajdują się elementy projektu, relacje elementów oraz skojarzone z nimi właściwości i polecenia.

 W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]programie zarządzanie hierarchiami projektów można zarządzać <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>za pomocą interfejsu hierarchii, . Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> przekierowuje wywoływane polecenia z elementów projektu do odpowiedniego okna hierarchii zamiast standardowego programu obsługi poleceń.

## <a name="project-hierarchies"></a>Hierarchie projektów
 Każda hierarchia projektów zawiera elementy, które można wyświetlać i edytować. Te elementy różnią się w zależności od typu projektu. Na przykład projekt bazy danych może zawierać procedury przechowywane, widoki bazy danych i tabele bazy danych. Projekt języka programowania, z drugiej strony, prawdopodobnie będzie zawierać pliki źródłowe i pliki zasobów dla map bitowych i okien dialogowych. Hierarchie mogą być zagnieżdżone, co zapewnia pewną większą elastyczność podczas tworzenia hierarchii projektu.

 Podczas tworzenia nowego typu projektu typ projektu steruje kompletnym zestawem elementów, które mogą być edytowane w nim. Jednak projekty mogą zawierać elementy, dla których nie mają obsługi edycji. Na przykład projekty języka Visual C++ mogą zawierać pliki HTML, nawet jeśli program Visual C++ nie udostępnia żadnego dostosowanego edytora dla typu pliku HTML.

 Hierarchie zarządzają trwałością elementów, które zawierają. Implementacja hierarchii musi kontrolować wszelkie specjalne właściwości, które wpływają na trwałość elementów w hierarchii. Na przykład jeśli elementy reprezentują obiekty w repozytorium zamiast plików, implementacja hierarchii musi kontrolować trwałość tych obiektów. Sam IDE kieruje hierarchii, aby zapisać elementy zgodnie z danymi wejściowymi użytkownika, ale IDE nie kontroluje żadnych akcji wymaganych do zapisania tych elementów. Zamiast tego projekt jest pod kontrolą.

 Gdy użytkownik otworzy element w edytorze, hierarchia, która kontroluje ten element jest zaznaczona i staje się aktywną hierarchią. Wybrana hierarchia określa zestaw poleceń dostępnych do działania na elemencie. Śledzenie fokus użytkownika w ten sposób umożliwia hierarchii, aby odzwierciedlić bieżący kontekst użytkownika.

## <a name="see-also"></a>Zobacz też
- [Typy projektów](../../extensibility/internals/project-types.md)
- [Wybór i waluta w IDEI](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Próbki VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
