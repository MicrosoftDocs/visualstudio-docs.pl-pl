---
title: Hierarchie
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2373909dbf218f24f148e0601d4dbb39cff1868
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061899"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchie w programie Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Zintegrowanego środowiska programistycznego (IDE) Wyświetla projektu jako *hierarchii*. W środowisku IDE programu hierarchii jest drzewo węzłów, w którym każdy węzeł ma zbiór skojarzonych z nimi właściwości. A *projektu hierarchii* to kontener, który zawiera elementy projektu, relacje elementów i skojarzonych z nimi właściwości elementów i polecenia.

 W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], zarządzanie hierarchiami projektu przy użyciu interfejsu hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Interfejsu przekierowuje wywołania z elementów projektu do okna odpowiedniej hierarchii zamiast programu obsługi poleceń standardowych poleceń.

## <a name="project-hierarchies"></a>Projekt hierarchii
 Każda hierarchia projektu zawiera elementy, które mogą wyświetlać i edytować. Te elementy różnią się w zależności od typu projektu. Na przykład projekt bazy danych może zawierać procedury składowane, widoki bazy danych i tabel bazy danych. Projekt język programowania, z drugiej strony, będzie prawdopodobnie zawierać pliki źródłowe i pliki zasobów dla mapy bitowe i w oknach dialogowych. Hierarchie mogą być zagnieżdżane, które zapewnia pewne dodatkową elastyczność podczas tworzenia hierarchii projektu.

 Gdy tworzysz nowy typ projektu, typ projektu określa kompletny zestaw elementów, które mogą być edytowane w nim. Jednak projekty mogą zawierać elementy, dla których nie mają edycję. Na przykład projektów Visual C++ może zawierać pliki HTML, mimo że Visual C++ nie zapewnia żadnych niestandardowy edytor dla typu pliku HTML.

 Hierarchie Zarządzanie trwałości elementy, które zawierają. Implementacja w hierarchii musi kontrolować specjalne właściwości, które wpływają na stan trwały elementów w hierarchii. Na przykład jeśli elementy reprezentują obiektów w repozytorium, a nie plików, wdrożenia hierarchii musi kontrolować trwałości tych obiektów. Bezpośrednio ze środowiska IDE kieruje hierarchii, aby zapisać elementy zgodne z danych wejściowych użytkownika, ale IDE nie jest kontrolowane przez dowolne operacje wymagane do zapisania tych elementów. Zamiast tego projektu jest w formancie.

 Gdy użytkownik otwiera element w edytorze, hierarchii, która kontroluje tego elementu jest zaznaczone i staje się aktywnej hierarchii. Wybrana hierarchia określa zestaw poleceń dostępnych do działania w elemencie. Śledzenie fokus w ten sposób umożliwia hierarchii, aby odzwierciedlić bieżący kontekst użytkownika.

## <a name="see-also"></a>Zobacz też
 [Typy projektów](../../extensibility/internals/project-types.md) [wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md) [przykłady VSSDK](../../misc/vssdk-samples.md)
