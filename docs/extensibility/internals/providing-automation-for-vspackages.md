---
title: Zapewnienie automatyzacji dla vspackages | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705946"
---
# <a name="providing-automation-for-vspackages"></a>Zapewnianie automatyzacji pakietów VSPackage
Istnieją dwa główne sposoby zapewnienia automatyzacji dla vsPackages: implementując vsPackage obiektów specyficznych dla i implementując standardowe obiekty automatyzacji. Ogólnie rzecz biorąc są one używane razem w celu rozszerzenia modelu automatyzacji środowiska.

## <a name="vspackage-specific-objects"></a>Obiekty specyficzne dla vspackage
 Niektóre miejsca w modelu automatyzacji wymagają zapewnienia automatyzacji obiektów, które są unikatowe dla vsPackage. Na przykład nowe projekty wymagają różnych obiektów, które zapewnia tylko vsPackage. Nazwy tych obiektów są wprowadzane w rejestrze i uzyskiwane za pośrednictwem wywołań do obiektu środowiska. `DTE`

 VSPackage specyficzne obiekty można również uzyskać, gdy konsument automatyzacji używa obiektu dostarczonego za pośrednictwem Object właściwości standardowego obiektu. Na przykład obiekt `Window` standardowy `Object` ma właściwość, `Windows.Object` znany powszechnie jako właściwość. Gdy konsumenci wywołać `Window.Object` w oknie zaimplementowanym w vsPackage, przekazać z powrotem określonego obiektu automatyzacji własnego projektu.

#### <a name="projects"></a>Projekty
 VsPackages można rozszerzyć model automatyzacji dla nowych typów projektów za pośrednictwem własnych VSPackage obiektów specyficznych dla programu. Głównym celem dostarczania nowych obiektów automatyzacji dla vsPackage jest rozróżnienie <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> unikatowych obiektów projektu od lub <xref:VSLangProj80.VSProject2> obiektu. To rozróżnienie jest przydatne, gdy chcesz zapewnić sposób wyodrębnić lub iteracji typu projektu oprócz innych typów projektów, powinny one pojawiają się obok siebie w rozwiązaniu. Aby uzyskać więcej informacji, zobacz [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Zdarzenia
 Architektura zdarzeń środowiska oferuje inne miejsce do dokowania własnych VSPackage specyficznych obiektów. Na przykład tworząc własne unikatowe obiekty zdarzeń, można rozszerzyć model zdarzeń środowiska dla projektów. Można podać własne zdarzenia, gdy nowy element jest dodawany do własnego typu projektu. Aby uzyskać więcej informacji, zobacz [Udostępnianie zdarzeń](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Obiekty okien
 System Windows może przekazać z powrotem obiekt automatyzacji specyficzne dla VSPackage z powrotem do środowiska, gdy wywoływane. Implementujesz obiekt, który jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> pochodną , lub `IDispatch` że ręce z powrotem właściwości, rozszerzenie obiektu okna, w którym jest on umiejscowiony. Na przykład można użyć tego podejścia, aby zapewnić automatyzację formantu umiejscowionych w ramce okna. Semantyka tego obiektu i innych obiektów, które mogą rozciągać się są twoje do projektowania. Aby uzyskać więcej informacji, zobacz [Jak: Zapewnienie automatyzacji dla systemu Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Strony z opcjami w menu Narzędzia
 Można tworzyć strony, aby rozszerzyć model automatyzacji Narzędzia, Opcje poprzez implementowanie stron i dodawanie informacji do rejestru, aby utworzyć własne opcje. Strony można następnie wywołać za pośrednictwem modelu obiektu środowiska, jak wszystkie inne strony opcji. Jeśli projekt funkcji, które są dodawany do środowiska za pośrednictwem VSPackages wymaga stron opcji, a następnie należy dodać obsługę automatyzacji, jak również. Aby uzyskać więcej informacji, zobacz [Obsługa automatyzacji stron opcji](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Standardowe obiekty automatyzacji
 Aby rozszerzyć automatyzację dla projektów, należy również zaimplementować standardowe obiekty automatyzacji (pochodzące z `IDispatch`), które stoją obok innych obiektów projektu i implementują standardowe metody i właściwości. Przykłady obiektów standardowych obejmują obiekty projektu wstawiane do `Projects`hierarchii rozwiązania, takie jak , `Project` `ProjectItem`, i `ProjectItems`. Każdy nowy typ projektu należy zaimplementować te obiekty (i ewentualnie inne w zależności od semantyki projektu).

 W pewnym sensie te obiekty zapewniają odwrotną zaletę vspackage obiektów projektu specyficzne. Standardowe obiekty automatyzacji umożliwiają projekt do użycia w sposób uogólniony, jak każdy inny projekt obsługujący te same obiekty. W związku z tym dodatek, który `Project` `ProjectItem` jest napisany względem ogólne i obiekty mogą działać przeciwko projektom dowolnego typu. Aby uzyskać więcej informacji, zobacz [Modelowanie projektu](../../extensibility/internals/project-modeling.md).
