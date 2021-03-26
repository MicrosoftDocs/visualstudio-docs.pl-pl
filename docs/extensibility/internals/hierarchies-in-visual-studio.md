---
title: Hierarchie w programie Visual Studio | Microsoft Docs
description: Informacje o hierarchiach projektów w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, które zawierają elementy projektu i ich skojarzone właściwości.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3fe1487e082907958c1cf8a36f1653efb97c9de
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056626"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchie w programie Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Zintegrowane środowisko programistyczne (IDE) wyświetla projekt jako *hierarchię*. W środowisku IDE hierarchia jest drzewem węzłów, gdzie każdy węzeł ma zestaw skojarzonych właściwości. *Hierarchia projektu* to kontener, który zawiera elementy projektu, relacje elementów i powiązane właściwości i polecenia elementów.

 W programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zarządzanie hierarchiami projektów jest możliwe za pomocą interfejsu hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Interfejs przekierowuje polecenia wywoływane z elementów projektu do odpowiedniego okna hierarchii zamiast standardowej procedury obsługi poleceń.

## <a name="project-hierarchies"></a>Hierarchie projektu
 Każda Hierarchia projektu zawiera elementy, które można wyświetlać i edytować. Te elementy różnią się w zależności od typu projektu. Na przykład projekt bazy danych może zawierać procedury składowane, widoki bazy danych i tabele baz danych. Z drugiej strony projekt języka programowania będzie prawdopodobnie obejmować pliki źródłowe i pliki zasobów dla map bitowych i okien dialogowych. Hierarchie mogą być zagnieżdżane, co daje pewną elastyczność podczas tworzenia hierarchii projektu.

 Podczas tworzenia nowego typu projektu typ projektu kontroluje kompletny zestaw elementów, które można edytować w nim. Jednak projekty mogą zawierać elementy, dla których nie mają obsługi edycji. Na przykład projekty Visual C++ mogą zawierać pliki HTML, nawet jeśli Visual C++ nie udostępnia żadnego niestandardowego edytora dla typu pliku HTML.

 Hierarchie zarządzają trwałość elementów, które zawierają. Implementacja hierarchii musi kontrolować wszystkie właściwości specjalne, które mają wpływ na trwałość elementów w hierarchii. Na przykład jeśli elementy reprezentują obiekty w repozytorium zamiast plików, implementacja hierarchii musi kontrolować trwałość tych obiektów. Samo środowisko IDE kieruje hierarchię do zapisania elementów zgodnych z danymi wejściowymi użytkownika, ale IDE nie kontroluje żadnych akcji wymaganych do zapisania tych elementów. Zamiast tego projekt jest w formancie.

 Gdy użytkownik otwiera element w edytorze, hierarchia kontrolująca ten element jest zaznaczona i zostaje uaktywniona. Wybrana hierarchia określa zestaw poleceń dostępnych do działania na elemencie. Śledzenie fokusu użytkownika w ten sposób umożliwia hierarchii odzwierciedlenie bieżącego kontekstu użytkownika.

## <a name="see-also"></a>Zobacz też
- [Typy projektów](../../extensibility/internals/project-types.md)
- [Wybór i waluta w IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Przykłady VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
