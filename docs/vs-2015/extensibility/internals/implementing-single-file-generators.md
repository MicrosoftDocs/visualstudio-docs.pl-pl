---
title: Implementowanie generatorów jednoplikowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36aa6df6c0b904ad11f0027c4e01368a9c864b8a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781676"
---
# <a name="implementing-single-file-generators"></a>Implementowanie generatorów jednoplikowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Narzędzie niestandardowe — czasami określane jako generator pojedynczego pliku — można używać do rozszerzenia [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] i [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektów systemów w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Niestandardowe narzędzie jest składnik modelu COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejsu. Przy użyciu tego interfejsu, niestandardowe narzędzie przekształca jeden plik wejściowy w pliku pojedynczego wyjścia. Wynik transformacji może być kod źródłowy lub inne dane wyjściowe, że jest to przydatne. Dwa przykłady plików niestandardowy kod wygenerowany przez narzędzie to kod wygenerowany w odpowiedzi na zmiany projektanta wizualnego i pliki generowane przy użyciu usługi sieci Web Services Description Language (WSDL).  
  
 Po załadowaniu niestandardowego narzędzia lub zapisaniu pliku wejściowego, system projektu wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metody i odwołuje się do <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfejs wywołania zwrotnego, według których narzędzie może raportować postęp do użytkownika.  
  
 Plik wyjściowy, generowany przez niestandardowe narzędzie zostanie dodany do projektu z zależnością od pliku wejściowego. System projektu automatycznie określa nazwę pliku wyjściowego na podstawie ciągu zwrócone przez narzędzie niestandardowe implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Niestandardowe narzędzie musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejsu. Opcjonalnie niestandardowego narzędzia obsługują <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfejsu do pobierania informacji ze źródła innego niż plik wejściowy. W każdym przypadku, zanim użyjesz narzędzie niestandardowe, należy zarejestrować go w systemie lub w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lokalnego rejestru. Aby uzyskać więcej informacji na temat rejestrowania niestandardowego narzędzia, zobacz [rejestrowanie generatorów jednoplikowych](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie Namespace domyślnego projektu](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)

