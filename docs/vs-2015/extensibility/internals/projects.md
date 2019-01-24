---
title: Projekty | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a251af12ccf4be5f0f48f789ac59fedaed3299b0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782734"
---
# <a name="projects"></a>Projekty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
 [Przykłady VSSDK](../../misc/vssdk-samples.md)  
 W tym artykule opisano próbek w VSSDK, które zajmują się projekty i rozwiązania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wewnątrz zestawu Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Opisano różne aspekty rozszerzeń programu Visual Studio.
