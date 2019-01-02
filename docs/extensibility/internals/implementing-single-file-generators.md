---
title: Implementowanie generatorów jednoplikowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 728a1748d4c78bd93bf827290404f65607076b6a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847785"
---
# <a name="implementing-single-file-generators"></a>Implementowanie generatorów jednoplikowych
Narzędzie niestandardowe — czasami określane jako generator pojedynczego pliku — można używać do rozszerzenia [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektów systemów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Niestandardowe narzędzie jest składnik modelu COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejsu. Przy użyciu tego interfejsu, niestandardowe narzędzie przekształca jeden plik wejściowy w pliku pojedynczego wyjścia. Wynik transformacji może być kod źródłowy lub inne dane wyjściowe, że jest to przydatne. Dwa przykłady plików niestandardowy kod wygenerowany przez narzędzie to kod wygenerowany w odpowiedzi na zmiany projektanta wizualnego i pliki generowane przy użyciu usługi sieci Web Services Description Language (WSDL).  
  
 Po załadowaniu niestandardowego narzędzia lub zapisaniu pliku wejściowego, system projektu wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metody i odwołuje się do <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfejs wywołania zwrotnego, według których narzędzie może raportować postęp do użytkownika.  
  
 Plik wyjściowy, generowany przez niestandardowe narzędzie zostanie dodany do projektu z zależnością od pliku wejściowego. System projektu automatycznie określa nazwę pliku wyjściowego na podstawie ciągu zwrócone przez narzędzie niestandardowe implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Niestandardowe narzędzie musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejsu. Opcjonalnie niestandardowego narzędzia obsługują <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfejsu do pobierania informacji ze źródła innego niż plik wejściowy. W każdym przypadku, zanim użyjesz narzędzie niestandardowe, należy zarejestrować go w systemie lub w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokalnego rejestru. Aby uzyskać więcej informacji na temat rejestrowania niestandardowego narzędzia, zobacz [rejestrowanie generatorów jednoplikowych](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)