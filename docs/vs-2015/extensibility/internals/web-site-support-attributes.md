---
title: Atrybuty obsługi witryny sieci Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144307"
---
# <a name="web-site-support-attributes"></a>Atrybuty pomocy technicznej dotyczącej witryn internetowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekt witryny sieci Web można rozszerzyć, aby zapewnić obsługę języków programowania w sieci Web. Język musi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] się zarejestrować w taki sposób, aby szablony projektu mogły pojawić się w oknie dialogowym **Nowa witryna sieci Web** w przypadku wybrania języka.  
  
 Przykład IronPython Studio obejmuje obsługę witryny sieci Web. Można go znaleźć za pomocą [przykładów VSSDK](../../misc/vssdk-samples.md). Zawiera następujące klasy atrybutów służące do rejestrowania IronPython jako język CodeBehind dla nowych projektów sieci Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Ten atrybut jest umieszczany w projekcie języka. Dodaje język do listy języków programowania w sieci Web na liście **Język** w oknie dialogowym **Nowa witryna sieci Web** . Na przykład następujące polecenie dodaje IronPython do listy:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Ten atrybut ustawia również ścieżkę szablonów, aby wskazywała folder szablonów. Aby uzyskać więcej informacji na temat lokalizacji folderu szablonów, zobacz [Szablony obsługi witryny sieci Web](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Ten atrybut jest umieszczany w projekcie języka. Umożliwia projekt witryny sieci Web zagnieżdżanie jednego typu pliku (powiązanego) pod innym typem pliku (podstawowego) w **Eksplorator rozwiązań**.  
  
 Na przykład:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Określa, że plik IronPython CodeBehind jest powiązany z plikiem. aspx. Gdy nowa strona sieci Web. aspx zostanie utworzona w rozwiązaniu witryny sieci Web IronPython, zostanie wygenerowany nowy plik źródłowy. pr.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Ten atrybut jest umieszczany w pakiecie projektu języka. Wybiera dostawcę IntelliSense dla danego języka.  
  
 Na przykład:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Określa, że wystąpienie PythonIntellisenseProvider, które implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , powinno być tworzone na żądanie w celu zapewnienia usług językowych.  
  
 Implementacja IVsIntellisenseProject obsługuje odwołania i wywołuje kompilator języka, gdy jest wymagana Strona sieci Web z kodem, ale nie jest buforowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)
