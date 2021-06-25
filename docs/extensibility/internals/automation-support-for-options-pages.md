---
title: Obsługa automatyzacji dla stron opcji | Microsoft Docs
description: Dowiedz się, jak udostępnić niestandardowe strony Opcji narzędzi w pakietach VSPackage Visual Studio modelu automatyzacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5a4f6b33b7a5e17c610831db5d4387065915ea00
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901659"
---
# <a name="automation-support-for-options-pages"></a>Obsługa automatyzacji dla stron Opcje
Pakiet VSPackages może udostępnić **niestandardowe** okna dialogowe Opcje **w** menu Narzędzia **(strony** Opcje narzędzi) w programie i udostępnić je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelowi automatyzacji.

## <a name="tools-options-pages"></a>strony opcji Narzędzi
 Aby utworzyć stronę **Opcje narzędzi,** pakiet VSPackage musi zapewnić implementację kontroli użytkownika zwróconą do środowiska za pośrednictwem implementacji metody vsPackage. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (Lub, w przypadku kodu zarządzanego, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metoda).

 Jest to opcjonalne, ale zdecydowanie zalecane, aby zezwolić na dostęp do tej nowej strony za pośrednictwem modelu automatyzacji. W tym celu wykonaj następujące czynności:

1. Rozszerzanie <xref:EnvDTE._DTE.Properties%2A> obiektu przez implementację obiektu pochodnego IDispatch.

2. Zwróć implementację metody (lub metody dla kodu zarządzanego) do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> obiektu pochodnego IDispatch.

3. Gdy konsument automatyzacji wywołuje metodę na niestandardowej stronie właściwości Option, środowisko używa metody w celu uzyskania niestandardowej implementacji automatyzacji strony Opcje <xref:EnvDTE._DTE.Properties%2A>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> narzędzi. 

4. Obiekt automatyzacji vsPackage jest następnie używany do zapewnienia każdego <xref:EnvDTE.Property> zwróconego przez <xref:EnvDTE._DTE.Properties%2A> .

   Aby uzyskać przykład implementacji niestandardowej **strony Opcje narzędzi,** zobacz [VsSDK Samples (Przykłady zestawu VSSDK).](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="see-also"></a>Zobacz też
- [Uwidocznij obiekty projektu](../../extensibility/internals/exposing-project-objects.md)
