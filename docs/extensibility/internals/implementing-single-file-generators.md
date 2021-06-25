---
title: Implementowanie Single-File generatorów | Microsoft Docs
description: Dowiedz się, jak używać niestandardowego narzędzia, które implementuje interfejs IVsSingleFileGenerator w celu rozszerzania systemów projektów Visual Basic i Visual C# w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ce8a69841d18d383e9d8e12c14d7af652d9cb8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900047"
---
# <a name="implementing-single-file-generators"></a>Implementowanie generatorów jednoplikowych
Narzędzie niestandardowe — czasami określane jako pojedynczy generator plików — może służyć do rozszerzania systemów [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu i w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Narzędzie niestandardowe to składnik COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejs. Za pomocą tego interfejsu narzędzie niestandardowe przekształca pojedynczy plik wejściowy w pojedynczy plik wyjściowy. Wynikiem przekształcenia może być kod źródłowy lub inne przydatne dane wyjściowe. Dwa przykłady niestandardowych plików kodu generowanych przez narzędzia to kod generowany w odpowiedzi na zmiany w projektancie wizualnym i pliki wygenerowane przy użyciu języka Web Services Description Language (WSDL).

 Po załadowaniu narzędzia niestandardowego lub zapisaniu pliku wejściowego system projektu wywołuje metodę i przekazuje odwołanie do interfejsu wywołania zwrotnego, dzięki któremu narzędzie może zgłaszać postęp <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> użytkownikowi.

 Plik wyjściowy generowany przez narzędzie niestandardowe jest dodawany do projektu z zależnością od pliku wejściowego. System projektu automatycznie określa nazwę pliku wyjściowego na podstawie ciągu zwróconego przez implementację narzędzia niestandardowego <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Niestandardowe narzędzie musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejs. Opcjonalnie narzędzia niestandardowe obsługują interfejs <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> do pobierania informacji ze źródeł innych niż plik wejściowy. W każdym przypadku przed użyciem narzędzia niestandardowego należy zarejestrować je w systemie lub [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w rejestrze lokalnym. Aby uzyskać więcej informacji na temat rejestrowania narzędzi niestandardowych, zobacz Registering Single File Generators (Rejestrowanie [generatorów pojedynczych plików).](../../extensibility/internals/registering-single-file-generators.md)

## <a name="see-also"></a>Zobacz też
- [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)
