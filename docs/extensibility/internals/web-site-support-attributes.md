---
title: Atrybuty pomocy technicznej dotyczącej witryn sieci Web | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac58ec0d7175d2d7989ce9c4d6086b5a741e77c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927245"
---
# <a name="web-site-support-attributes"></a>Atrybuty pomocy technicznej dotyczącej witryn internetowych
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt witryny sieci Web można rozszerzony w celu zapewnienia wsparcia dla sieci Web, języków programowania. Język musi zarejestrować się przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, aby szablonów projektu może znajdować się w **nową witrynę sieci Web** okno dialogowe po wybraniu języka.

Przykład IronPython Studio obejmuje obsługę witryny sieci web. Przykład zawiera następujące klasy atrybutu do zarejestrowania IronPython jako język codebehind dla nowych projektów sieci Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Ten atrybut jest umieszczany w projekcie języka. Dodaje do listy języków programowania w sieci Web języka **języka** listy w **nową witrynę sieci Web** okno dialogowe. Na przykład poniższy kod dodaje IronPython do listy:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Ten atrybut ustawia również ścieżki szablonów, by wskazywał folder szablonów. Aby uzyskać więcej informacji na temat lokalizacji folderu szablonów, zobacz [witryny sieci Web pomocy technicznej szablony](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Ten atrybut jest umieszczany w projekcie języka. Pozwala ono projektu witryny sieci Web zagnieździć jednego typu pliku (powiązane) w ramach innego typu pliku (podstawowy) **Eksploratora rozwiązań**.

 Na przykład poniższy kod określa, czy plik codebehind IronPython jest powiązany z pliku .aspx. Po utworzeniu nowej strony sieci Web .aspx w rozwiązaniu witryny sieci IronPython Web nowy plik źródłowy PY zostanie wygenerowany i jest wyświetlany jako elementem podrzędnym strony .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Ten atrybut jest umieszczany na pakietu projektu języka. Wybiera dostawcę funkcji IntelliSense dla języka.

 Na przykład, poniższy kod określa, że wystąpienie PythonIntellisenseProvider, która implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, należy utworzyć na żądanie do usługi języka.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Implementacja IVsIntellisenseProject obsługuje odwołania i wywołuje kompilator języka, gdy żądania strony sieci Web przy użyciu kodu, ale nie są buforowane.

## <a name="see-also"></a>Zobacz też
 [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)