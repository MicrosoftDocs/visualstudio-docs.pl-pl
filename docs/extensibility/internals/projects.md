---
title: Projekty | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706211"
---
# <a name="projects"></a>Projekty
W programie Visual Studio projekty są kontenerami używanymi przez deweloperów do organizowania plików kodu źródłowego i innych zasobów wyświetlanych w **Eksploratorze rozwiązań.** Zazwyczaj projekty są plikami (na przykład pliki .csproj dla projektu C#), które przechowują odwołania do plików kodu źródłowego i zasobów, takich jak pliki bitmapowe. Projekty umożliwiają organizowanie, tworzenie, debugowanie i wdrażanie kodu źródłowego, odwołania do usług sieci Web i baz danych oraz innych zasobów. VsPackages można rozszerzyć system projektu Visual Studio na trzy główne sposoby: *typy projektów*, *podtypy projektu*i *narzędzia niestandardowe*.

## <a name="in-this-section"></a>W tej sekcji
- [Project Types (Typy projektów)](../../extensibility/internals/project-types.md)

 *Typy projektów* dodać obsługę nowych rodzajów projektów, takich jak języki programowania. Na przykład każdy język, który obsługuje visual studio ma swój własny typ projektu, a przykład integracji IronPython zawiera typ projektu dla języka IronPython. Należy utworzyć typ projektu dla języków innych niż C# lub Visual Basic, aby dostosować sposób tworzenia, debugowania, wdrażania i wyświetlania elementów w **Eksploratorze rozwiązań**. Aby uzyskać więcej informacji, zobacz [Typy projektów](../../extensibility/internals/project-types.md).

- [Podtypy projektów](../../extensibility/internals/project-subtypes.md)

 *Podtypy projektu* są oparte na typach projektów i mogą służyć do dostosowywania sposobu, w jaki projekty są tworzone, debugowane i wdrażane. Program Visual Studio używa podtypów projektu z projektami urządzenia inteligentnego; dostosowują wdrożenie, kopiując nowo utworzony program z komputera dewelopera do urządzenia docelowego. Typy projektów Języka C# i Visual Basic mogą służyć jako podstawa dla podtypów projektu; Nie można typów projektów języka C++. Własne typy projektów mogą być również używane jako podstawa dla podtypów projektu. Aby uzyskać więcej informacji, zobacz [Podtypy projektu](../../extensibility/internals/project-subtypes.md).

- [Projekty internetowe](../../extensibility/internals/web-projects.md)

 W tym artykule wyjaśniono projekt sieci Web, który z kolei tworzy aplikacje sieci Web.

- [Nowa generacja projektów: Pod maską, część pierwsza](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) i [nowa generacja projektu: pod maską, część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Wyjaśniono, co faktycznie występuje podczas tworzenia nowego projektu.

- [Próbki VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Zawiera przykłady w vssdk, które zajmują się projektami i rozwiązaniami.

## <a name="related-sections"></a>Sekcje pokrewne
- [Wewnątrz zestawu Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Wyjaśnij różne aspekty rozszerzalności programu Visual Studio.
