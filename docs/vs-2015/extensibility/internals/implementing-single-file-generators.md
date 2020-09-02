---
title: Implementowanie generatorów pojedynczych plików | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192691"
---
# <a name="implementing-single-file-generators"></a>Implementowanie generatorów jednoplikowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Niestandardowe narzędzie — czasami nazywane generatorem pojedynczego pliku — może służyć do rozbudowania [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] systemów i projektów w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Narzędzie niestandardowe jest składnikiem COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejs. Korzystając z tego interfejsu, narzędzie niestandardowe przekształca pojedynczy plik wejściowy w jeden plik wyjściowy. Wynikiem przekształcenia może być kod źródłowy lub inne dane wyjściowe, które są użyteczne. Dwa przykłady niestandardowych plików kodu generowanego przez narzędzie to kod generowany w odpowiedzi na zmiany w projektancie wizualnym i pliki generowane przy użyciu Web Services Description Language (WSDL).  
  
 Po załadowaniu niestandardowego narzędzia lub zapisaniu pliku wejściowego system projektu wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metodę i przekazuje odwołanie do <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfejsu wywołania zwrotnego, zgodnie z którym narzędzie może zgłosić postęp użytkownikowi.  
  
 Plik wyjściowy, który generuje narzędzie niestandardowe, jest dodawany do projektu z zależnością od pliku wejściowego. System projektu automatycznie określa nazwę pliku wyjściowego na podstawie ciągu zwracanego przez implementację niestandardowego narzędzia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .  
  
 Narzędzie niestandardowe musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejs. Opcjonalnie narzędzia niestandardowe obsługują <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfejs do pobierania informacji ze źródeł innych niż plik wejściowy. W każdym przypadku, zanim będzie można użyć narzędzia niestandardowego, należy zarejestrować je w systemie lub w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rejestrze lokalnym. Aby uzyskać więcej informacji na temat rejestrowania narzędzi niestandardowych, zobacz [Rejestrowanie generatorów pojedynczych plików](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie domyślnej przestrzeni nazw projektu](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)
