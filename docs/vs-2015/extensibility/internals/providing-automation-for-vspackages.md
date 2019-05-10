---
title: Zapewnianie automatyzacji pakietów VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6eb76eba76567f2966323d4058c9e752cb6fb69
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777539"
---
# <a name="providing-automation-for-vspackages"></a>Zapewnianie automatyzacji pakietów VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Istnieją dwa główne sposoby zapewnienia automatyzacji z pakietów VSPackage: wdrażając obiektów specyficznych dla pakietu VSPackage i wdrażając obiektów automatyzacji w wersji standard. Ogólnie rzecz biorąc są one używane razem do rozszerzenia modelu automatyzacji środowiska.  
  
## <a name="vspackage-specific-objects"></a>VSPackage-Specific Objects  
 Niektóre miejsca, w ramach modelu automatyzacji wymagają podania obiektów automatyzacji, które są unikatowe dla Twojego pakietu VSPackage. Na przykład nowe projekty wymagają różnych obiektów, które zawiera tylko Twojego pakietu VSPackage. Nazwy tych obiektów są wprowadzane w rejestrze i pobierane za pośrednictwem wywołania w środowisku `DTE` obiektu.  
  
 Obiektów specyficznych dla pakietu VSPackage można także uzyskać, gdy konsumenta automatyzacji używa obiektu, dostępne za pośrednictwem właściwości obiektu standardowego obiektu. Na przykład standardowy `Window` obiekt ma `Object` właściwość, powszechnie znane jako `Windows.Object` właściwości. Gdy konsumenci wywołana `Window.Object` w oknie, zaimplementowane w swojej pakietu VSPackage, możesz przesłać obiekt automatyzacji określonego własnego projektu.  
  
#### <a name="projects"></a>Projekty  
 Model automatyzacji do nowych typów projektów za pomocą ich własnych obiektów specyficznych dla pakietu VSPackage rozszerzyć pakietów VSPackage. Głównym celem dostarczanie nowych obiektów automatyzacji dla Twojego pakietu VSPackage to odróżnić unikatowy projektu obiekty <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> lub <xref:VSLangProj80.VSProject2> obiektu. To zróżnicowanie jest przydatne, gdy chcesz umożliwiają wyróżnia lub iteracji danego typu projektu, niezależnie od innych typów projektów należy pojawiają się side-by-side w rozwiązaniu. Aby uzyskać więcej informacji, zobacz [udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Zdarzenia  
 Architektura zdarzeń środowiska oferuje inną pozwalający na dołączanie obiektów specyficznych dla pakietu VSPackage. Na przykład przez utworzenie własnych obiektów unikatowego wydarzenia, można rozszerzyć środowisko modelu zdarzeń dla projektów. Możesz podać własne zdarzenia, gdy nowy element zostanie dodany do swój własny typ projektu. Aby uzyskać więcej informacji, zobacz [udostępnianie zdarzeń](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Obiekty okien  
 Windows można przesłać obiektu automatyzacji specyficzne dla pakietu VSPackage do środowiska, gdy zostanie wywołana. Implementowanie obiekt, który jest tworzony na podstawie <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> lub `IDispatch` ponownie przekazuje właściwości, rozszerzając obiekt okna, w którym jest ulokowany. Na przykład umożliwia to podejście zapewnianie automatyzacji dla formantu ulokowany ramki okna. Semantyka tego obiektu i inne obiekty, które go może wydłużyć są Twoje do projektowania. Aby uzyskać więcej informacji, zobacz [jak: Zapewnianie automatyzacji dla Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Strony opcji w menu Narzędzia  
 Można utworzyć strony, aby rozszerzyć opcje modelu automatyzacji za pośrednictwem Implementowanie strony i dodawanie informacji do rejestru w celu tworzenia własnych opcji w menu Narzędzia. Następnie można wywołać strony za pomocą modelu obiektów środowiska, takie jak innych stron opcji. Projektowanie funkcji, którą chcesz dodać do środowiska za pomocą pakietów VSPackage wymaga stron opcji, należy dodać także obsługa automatyzacji. Aby uzyskać więcej informacji, zobacz [Obsługa automatyzacji dla stron opcji](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Obiekty automatyzacji w wersji Standard  
 Aby rozszerzyć automatyzacji dla projektów, także implementować obiektów automatyzacji w wersji standard (pochodną `IDispatch`) który autonomiczna obok innych obiektów projektu i implementacji standardowych metod i właściwości. Standardowe obiekty przykłady obiektów projektu, które są wstawiane do hierarchii rozwiązania, takie jak `Projects`, `Project`, `ProjectItem`, i `ProjectItems`. Każdy nowy typ projektu powinny implementować te obiekty (i ewentualnie inne z nich, w zależności od semantykę projektu).  
  
 W tym sensie te obiekty oferują przeciwny zalet obiektów projektu specyficznych dla pakietu VSPackage. Obiekty automatyzacji w wersji standard umożliwia projekt ma być używany w sposób uogólniony, podobnie jak każdy inny projekt, obsługuje te same obiekty. W związku z tym, dodatek napisany przeciwko ogólne `Project` i `ProjectItem` obiektów może działać względem projektów dowolnego typu. Aby uzyskać więcej informacji, zobacz [projektu modelowania](../../extensibility/internals/project-modeling.md).
