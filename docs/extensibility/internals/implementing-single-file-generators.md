---
title: Implementowanie generatorów pojedynczych plików | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69bde665e62d063b6bab8784634777eeea02e941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727175"
---
# <a name="implementing-single-file-generators"></a>Implementowanie generatorów jednoplikowych
Niestandardowe narzędzie — czasami nazywane generatorem pojedynczego pliku — może służyć do rozbudowania [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] systemów projektu w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Narzędzie niestandardowe jest składnikiem COM, który implementuje interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Korzystając z tego interfejsu, narzędzie niestandardowe przekształca pojedynczy plik wejściowy w jeden plik wyjściowy. Wynikiem przekształcenia może być kod źródłowy lub inne dane wyjściowe, które są użyteczne. Dwa przykłady niestandardowych plików kodu generowanego przez narzędzie to kod generowany w odpowiedzi na zmiany w projektancie wizualnym i pliki generowane przy użyciu Web Services Description Language (WSDL).

 Po załadowaniu niestandardowego narzędzia lub zapisaniu pliku wejściowego system projektu wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> i przekazuje odwołanie do interfejsu wywołania zwrotnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>, dzięki czemu narzędzie może zgłosić postęp użytkownikowi.

 Plik wyjściowy, który generuje narzędzie niestandardowe, jest dodawany do projektu z zależnością od pliku wejściowego. System projektu automatycznie określa nazwę pliku wyjściowego na podstawie ciągu zwracanego przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> niestandardowego narzędzia.

 Narzędzie niestandardowe musi implementować interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Opcjonalnie narzędzia niestandardowe obsługują interfejs <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>, aby pobrać informacje ze źródeł innych niż plik wejściowy. W każdym przypadku, zanim będzie można użyć narzędzia niestandardowego, należy zarejestrować je w systemie lub w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokalnym rejestrze. Aby uzyskać więcej informacji na temat rejestrowania narzędzi niestandardowych, zobacz [Rejestrowanie generatorów pojedynczych plików](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Zobacz także
- [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)