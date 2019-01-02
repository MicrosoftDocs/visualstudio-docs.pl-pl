---
title: Projekty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 893dbdb8a1ff92d338b6e8ee654f60578990c7e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876747"
---
# <a name="projects"></a>Projekty
W programie Visual Studio, projekty są kontenerami, używanych przez deweloperów do organizowania plików kodu źródłowego i inne zasoby, które pojawiają się w **Eksploratora rozwiązań**. Zazwyczaj projekty są plikami (na przykład plik .csproj, które projektu C#), które są przechowywane odwołania do plików kodu źródłowego i zasobów, takich jak pliki map bitowych. Projekty umożliwiają organizowanie, kompilowanie, debugowanie i wdróż kod źródłowy, odwołuje się do usługi sieci Web i baz danych i innych zasobów. Pakietów VSPackage można rozszerzyć system projektu programu Visual Studio w na trzy sposoby: *typów projektów*, *podtypy projektów*, i *narzędzia niestandardowe*.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 *Typy projektów* dodano obsługę nowych rodzajów projektów, takich jak języki programowania. Na przykład każdy język, który obsługuje Visual Studio ma swój własny typ projektu, a przykład integracji IronPython zawiera typ projektu dla języka IronPython. Należy utworzyć typ projektu w językach innych niż C# lub Visual Basic można dostosować, jak elementy są wbudowane, debugować, wdrożyć i wyświetlane w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [typów projektów](../../extensibility/internals/project-types.md).  
  
 [Podtypy projektów](../../extensibility/internals/project-subtypes.md)  
 *Podtypy projektów* są oparte na typach projektów i pozwala dostosować sposób projekty są wbudowane, debugować i wdrażane. Program Visual Studio używa podtypy projektów, projektów urządzeń inteligentnych; wdrożenia mogą dostosować przez skopiowanie program nowo utworzone z komputera, na urządzeniu docelowym. C# i typów projektów języka Visual Basic może służyć jako podstawa dla podtypy projektów; Nie można typów projektów języka C++. Swój własny typ projektu można również jako podstawy dla podtypy projektów. Aby uzyskać więcej informacji, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).  
  
 [Projekty internetowe](../../extensibility/internals/web-projects.md)  
 W tym artykule wyjaśniono projektu sieci Web, który z kolei tworzyć aplikacje sieci Web.  
  
 [Generowanie nowego projektu: Za kulisami, część jednego](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) i [Generowanie nowego projektu: Kulisami część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 W tym artykule wyjaśniono, jakie rzeczywiście występuje podczas tworzenia nowego projektu.  
  
 [Przykłady VSSDK](http://aka.ms/vs2015sdksamples)  
 Zawiera przykłady w VSSDK, które zajmują się projekty i rozwiązania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wewnątrz zestawu Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Opisano różne aspekty rozszerzeń programu Visual Studio.