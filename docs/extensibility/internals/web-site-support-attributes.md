---
title: Atrybuty obsługi witryny sieci Web | Microsoft Docs
description: Dowiedz się więcej o atrybutach obsługi witryny sieci Web, które są niezbędne do rozszerzenia funkcjonalności usługi Visual Studio przy użyciu projektów witryn sieci Web.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 348fd16234e38cd7832ae18e7b28e6abe0bc63d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901776"
---
# <a name="web-site-support-attributes"></a>Atrybuty pomocy technicznej dotyczącej witryn internetowych
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt witryny sieci Web można rozszerzyć w celu zapewnienia obsługi języków programowania w sieci Web. Język musi zostać zarejestrowany przy użyciu funkcji , aby szablony projektu można było wyświetlać w oknie dialogowym Nowa witryna sieci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Web** po wybraniu języka.

Przykład IronPython Studio obejmuje obsługę witryn internetowych. Przykład zawiera następujące klasy atrybutów służące do rejestrowania ironpython jako języka codebehind dla nowych projektów internetowych.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Ten atrybut jest umieszczany w projekcie języka. Dodaje język do listy języków programowania sieci Web na **liście** Język w oknie dialogowym **Nowa witryna** sieci Web. Na przykład poniższy kod dodaje do listy ironpython:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Ten atrybut ustawia również ścieżkę szablonów tak, aby wskazać folder szablonów. Aby uzyskać więcej informacji na temat lokalizacji folderu templates, zobacz [Szablony pomocy technicznej witryny sieci Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Ten atrybut jest umieszczany w projekcie języka. Umożliwia on projektowi witryny sieci Web zagnieżdżanie jednego typu pliku (powiązanego) w innym typie pliku (podstawowym) w Eksplorator rozwiązań **.**

 Na przykład poniższy kod określa, że plik codebehind IronPython jest powiązany z plikiem aspx. Po utworzeniu nowej strony internetowej aspx w rozwiązaniu witryny internetowej IronPython generowany jest nowy plik źródłowy PY, który jest wyświetlany jako węzeł podrzędny na stronie aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Ten atrybut jest umieszczany w pakiecie projektu języka. Wybiera ona dostawcę funkcji IntelliSense dla języka.

 Na przykład poniższy kod określa, że wystąpienie klasy PythonIntellisenseProvider, które implementuje element , powinno zostać utworzone na żądanie w celu <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> zapewnienia usług językowych.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Implementacja IVsIntellisenseProject obsługuje odwołania i wywołuje kompilator języka, gdy żądana jest strona internetowa z kodem, ale nie jest buforowana.

## <a name="see-also"></a>Zobacz też
- [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)
