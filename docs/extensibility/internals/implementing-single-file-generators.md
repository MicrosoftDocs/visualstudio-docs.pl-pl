---
title: Wdrażanie generatorów jednopłećowych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707657"
---
# <a name="implementing-single-file-generators"></a>Implementowanie generatorów jednoplikowych
Niestandardowe narzędzie — czasami nazywane pojedynczym generatorem plików [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] — może [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]być używane do rozszerzania systemów projektu w programie . Narzędzie niestandardowe jest składnikiem COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejs. Za pomocą tego interfejsu narzędzie niestandardowe przekształca pojedynczy plik wejściowy w jeden plik wyjściowy. Wynikiem transformacji może być kod źródłowy lub inne dane wyjściowe, które są przydatne. Dwa przykłady niestandardowych plików kodu generowanych przez narzędzia są kod generowany w odpowiedzi na zmiany w projektancie wizualnym i pliki generowane przy użyciu języka opisu usług sieci Web (WSDL).

 Po załadowaniu narzędzia niestandardowego lub zapisaniu pliku wejściowego <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> system projektu wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> i przekazuje odwołanie do interfejsu wywołania zwrotnego, dzięki czemu narzędzie może zgłaszać swój postęp użytkownikowi.

 Plik wyjściowy, który generuje narzędzie niestandardowe jest dodawany do projektu z zależnością od pliku wejściowego. System projektu automatycznie określa nazwę pliku wyjściowego na podstawie ciągu zwróconego przez implementację narzędzia niestandardowego <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.

 Narzędzie niestandardowe musi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> implementować interfejs. Opcjonalnie narzędzia niestandardowe <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> obsługują interfejs do pobierania informacji ze źródeł innych niż plik wejściowy. W każdym przypadku, zanim będzie można użyć narzędzia niestandardowego, należy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zarejestrować go w systemie lub w rejestrze lokalnym. Aby uzyskać więcej informacji na temat rejestrowania narzędzi niestandardowych, zobacz [Rejestrowanie generatorów pojedynczych plików](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Zobacz też
- [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)
