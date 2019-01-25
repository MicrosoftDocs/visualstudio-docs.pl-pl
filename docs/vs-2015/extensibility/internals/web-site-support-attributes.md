---
title: Atrybuty pomocy technicznej dotyczącej witryn sieci Web | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779380"
---
# <a name="web-site-support-attributes"></a>Atrybuty pomocy technicznej dotyczącej witryn internetowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekt witryny sieci Web można rozszerzony w celu zapewnienia wsparcia dla sieci Web, języków programowania. Język musi zarejestrować się przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tak, aby szablonów projektu może znajdować się w **nową witrynę sieci Web** okno dialogowe po wybraniu języka.  
  
 Przykład IronPython Studio obejmuje obsługę witryny sieci web. Znajdziesz go za pomocą [przykłady VSSDK](../../misc/vssdk-samples.md). Obejmuje następujące klasy atrybutu do zarejestrowania IronPython jako język codebehind dla nowych projektów sieci Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Ten atrybut jest umieszczany w projekcie języka. Dodaje do listy języków programowania w sieci Web języka **języka** listy w **nową witrynę sieci Web** okno dialogowe. Na przykład następujące o rozmiarze IronPython do listy:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Ten atrybut ustawia również ścieżki szablonów, by wskazywał folder szablonów. Aby uzyskać więcej informacji na temat lokalizacji folderu szablonów, zobacz [witryny sieci Web pomocy technicznej szablony](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Ten atrybut jest umieszczany w projekcie języka. Pozwala ono projektu witryny sieci Web zagnieździć jednego typu pliku (powiązane) w ramach innego typu pliku (podstawowy) **Eksploratora rozwiązań**.  
  
 Na przykład:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Określa, czy plik codebehind IronPython jest powiązany z pliku .aspx. Po utworzeniu nowej strony sieci Web .aspx w rozwiązaniu witryny sieci IronPython Web nowy plik źródłowy PY zostanie wygenerowany i jest wyświetlany jako elementem podrzędnym strony .aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Ten atrybut jest umieszczany na pakietu projektu języka. Wybiera dostawcę funkcji Intellisense dla języka.  
  
 Na przykład:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Określa, że wystąpienie PythonIntellisenseProvider, która implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, należy utworzyć na żądanie do usługi języka.  
  
 Implementacja IVsIntellisenseProject obsługuje odwołania i wywołuje kompilator języka, gdy żądania strony sieci Web przy użyciu kodu, ale nie jest buforowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)
