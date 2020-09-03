---
title: Dostarczanie automatyzacji dla pakietów VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705946"
---
# <a name="providing-automation-for-vspackages"></a>Zapewnianie automatyzacji pakietów VSPackage
Istnieją dwa podstawowe sposoby zapewnienia automatyzacji dla pakietów VSPackage: przez implementację obiektów pakietu VSPackage i implementowanie standardowych obiektów automatyzacji. Ogólnie rzecz biorąc, są one używane razem w celu rozbudowania modelu automatyzacji środowiska.

## <a name="vspackage-specific-objects"></a>Pakietu VSPackage — obiekty
 Niektóre miejsca w modelu automatyzacji wymagają podania obiektów automatyzacji, które są unikatowe dla pakietu VSPackage. Na przykład nowe projekty wymagają odrębnych obiektów, które są dostępne tylko dla pakietu VSPackage. Nazwy tych obiektów są wprowadzane w rejestrze i uzyskiwane za pomocą wywołań do `DTE` obiektu Environment.

 Obiektów specyficznych dla pakietu VSPackage można także uzyskać, gdy odbiorca usługi Automation używa obiektu dostarczonego za pośrednictwem właściwości Object obiektu standardowego. Na przykład `Window` obiekt standardowy ma `Object` Właściwość, znaną często jako `Windows.Object` Właściwość. Gdy konsumenci wywołują w `Window.Object` oknie zaimplementowanym w pakietu VSPackage, przekazujesz określony obiekt automatyzacji własny projekt.

#### <a name="projects"></a>Projekty
 Pakietów VSPackage może zwiększyć model automatyzacji dla nowych typów projektów za pomocą własnych obiektów pakietu VSPackage. Głównym celem udostępniania nowych obiektów automatyzacji dla pakietu VSPackage jest odróżnienie unikatowych obiektów projektu od <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> lub do <xref:VSLangProj80.VSProject2> obiektu. To zróżnicowanie jest przydatne, gdy chcesz zapewnić możliwość jednokrotnego lub iteracji typu projektu poza innymi typami projektów, jeśli są one widoczne obok siebie w rozwiązaniu. Aby uzyskać więcej informacji, zobacz [udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Zdarzenia
 Architektura zdarzeń środowiska oferuje inne miejsce do dołączania własnych obiektów pakietu VSPackage. Na przykład poprzez utworzenie własnych unikatowych obiektów zdarzeń można zwiększyć model zdarzeń środowiska dla projektów. Możesz chcieć podać własne zdarzenia, gdy nowy element zostanie dodany do własnego typu projektu. Aby uzyskać więcej informacji, zobacz [udostępnianie zdarzeń](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Obiekty okien
 System Windows może przekazać obiekt automatyzacji określony przez pakietu VSPackage z powrotem do środowiska po wywołaniu. Zaimplementowanie obiektu, który jest pochodną <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> lub `IDispatch` właściwościami z powrotem, rozszerzanie obiektu okna, w którym jest zlokalizowany. Można na przykład użyć tej metody w celu zapewnienia automatyzacji dla kontrolki znajdującej się w ramce okna. Semantyką tego obiektu i wszelkich innych obiektów, które mogą zostać rozbudowane, jest projektowanie. Aby uzyskać więcej informacji, zobacz [How to: zapewnianie automatyzacji dla systemu Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Strony opcji w menu Narzędzia
 Można utworzyć strony, aby rozłożyć narzędzia, opcje modelu automatyzacji przez implementację stron i dodać informacje do rejestru w celu utworzenia własnych opcji. Strony można następnie wywołać za pomocą modelu obiektów środowiska, takiego jak wszystkie inne strony opcji. Jeśli projekt funkcji dodawanej do środowiska za pomocą pakietów VSPackage wymaga stron opcji, należy również dodać obsługę automatyzacji. Aby uzyskać więcej informacji, zobacz [Obsługa automatyzacji dla stron opcji](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Obiekty automatyzacji w warstwie Standardowa
 Aby rozszerzać automatyzację projektów, należy również zaimplementować standardowe obiekty automatyzacji (pochodzące z `IDispatch` ), które są obok innych obiektów projektu i implementują standardowe metody i właściwości. Przykłady standardowych obiektów obejmują obiekty projektu, które są wstawiane do hierarchii rozwiązań, takich jak `Projects` , `Project` , `ProjectItem` i `ProjectItems` . Każdy nowy typ projektu powinien implementować te obiekty (i ewentualnie inne w zależności od semantyki projektu).

 W sensie te obiekty zapewniają odwrotną korzyść obiektów projektu specyficznych dla pakietu VSPackage. Standardowe obiekty automatyzacji umożliwiają użycie projektu w ogólny sposób, jak każdy inny projekt obsługujący te same obiekty. W ten sposób dodatek, który jest zapisywana względem ogólnych `Project` i `ProjectItem` obiektów, może działać z projektami dowolnego typu. Aby uzyskać więcej informacji, zobacz artykuł [Modeling Project](../../extensibility/internals/project-modeling.md).
