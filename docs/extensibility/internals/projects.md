---
title: Projekty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706211"
---
# <a name="projects"></a>Projekty
W programie Visual Studio projekty są kontenerami używanymi przez deweloperów do organizowania plików kodu źródłowego i innych zasobów, które są wyświetlane w **Eksplorator rozwiązań**. Zazwyczaj projekty są plikami (na przykład plik. csproj dla projektu C#), który przechowuje odwołania do plików kodu źródłowego i zasobów, takich jak pliki map bitowych. Projekty umożliwiają organizowanie, kompilowanie, debugowanie i wdrażanie kodu źródłowego, odwołań do usług sieci Web i baz danych oraz innych zasobów. Pakietów VSPackage może rozciągnąć system projektu programu Visual Studio na trzy główne sposoby: *typy projektów*, *podtypy projektu*i *narzędzia niestandardowe*.

## <a name="in-this-section"></a>W tej sekcji
- [Typy projektów](../../extensibility/internals/project-types.md)

 *Typy projektów* dodają obsługę nowych rodzajów projektów, takich jak języki programowania. Na przykład każdy język obsługiwany przez program Visual Studio ma własny typ projektu, a przykład integracji IronPython zawiera typ projektu dla języka IronPython. Należy utworzyć typ projektu dla języków innych niż C# lub Visual Basic, aby dostosować sposób kompilowania, debugowania, wdrażania i wyświetlania elementów w programie **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [typy projektów](../../extensibility/internals/project-types.md).

- [Podtypy projektów](../../extensibility/internals/project-subtypes.md)

 *Podtypy projektu* są oparte na typach projektów i można ich użyć do dostosowania sposobu, w jaki projekty są kompilowane, debugowane i wdrażane. Program Visual Studio używa podtypów projektów z inteligentnymi projektami urządzeń; dostosowuje wdrożenie przez skopiowanie nowo skompilowanego programu z komputera deweloperskiego na urządzenie docelowe. Typy projektów C# i Visual Basic mogą być używane jako podstawa dla podtypów projektu; Typy projektów C++ nie mogą. Własne typy projektów mogą być również używane jako podstawa dla podtypów projektu. Aby uzyskać więcej informacji, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).

- [Projekty internetowe](../../extensibility/internals/web-projects.md)

 Objaśnia projekt sieci Web, który z kolei umożliwia tworzenie aplikacji sieci Web.

- [Generowanie nowego projektu: pod okapem, część jednej](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) i [Nowa generacja projektu: pod okapem, część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Wyjaśnia, co faktycznie występuje podczas tworzenia nowego projektu.

- [Przykłady VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Zawiera przykłady w VSSDK, które zajmują się projektami i rozwiązaniami.

## <a name="related-sections"></a>Sekcje pokrewne
- [Wewnątrz zestawu Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Wyjaśnij różne aspekty rozszerzalności programu Visual Studio.
