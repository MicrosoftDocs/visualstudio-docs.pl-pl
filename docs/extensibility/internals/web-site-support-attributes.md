---
title: Atrybuty obsługi witryny sieci Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07486ea3a962bcb81f65ad0b61ea2e41b3248678
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721608"
---
# <a name="web-site-support-attributes"></a>Atrybuty pomocy technicznej dotyczącej witryn internetowych
projekt witryny sieci Web [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można rozszerzyć, aby zapewnić obsługę języków programowania sieci Web. Język musi się zarejestrować w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], aby szablony projektu mogły pojawić się w oknie dialogowym **Nowa witryna sieci Web** w przypadku wybrania języka.

Przykład IronPython Studio obejmuje obsługę witryny sieci Web. Przykład zawiera następujące klasy atrybutów, aby zarejestrować IronPython jako język CodeBehind dla nowych projektów sieci Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Ten atrybut jest umieszczany w projekcie języka. Dodaje język do listy języków programowania w sieci Web na liście **Język** w oknie dialogowym **Nowa witryna sieci Web** . Na przykład poniższy kod dodaje IronPython do listy:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Ten atrybut ustawia również ścieżkę szablonów, aby wskazywała folder szablonów. Aby uzyskać więcej informacji na temat lokalizacji folderu szablonów, zobacz [Szablony obsługi witryny sieci Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Ten atrybut jest umieszczany w projekcie języka. Umożliwia projekt witryny sieci Web zagnieżdżanie jednego typu pliku (powiązanego) pod innym typem pliku (podstawowego) w **Eksplorator rozwiązań**.

 Na przykład poniższy kod określa, że plik IronPython CodeBehind jest powiązany z plikiem. aspx. Gdy nowa strona sieci Web. aspx zostanie utworzona w rozwiązaniu witryny sieci Web IronPython, zostanie wygenerowany nowy plik źródłowy. pr.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Ten atrybut jest umieszczany w pakiecie projektu języka. Wybiera dostawcę IntelliSense dla danego języka.

 Na przykład poniższy kod określa, że wystąpienie PythonIntellisenseProvider, które implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, powinno być tworzone na żądanie w celu zapewnienia usług językowych.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Implementacja IVsIntellisenseProject obsługuje odwołania i wywołuje kompilator języka, gdy jest wymagana Strona sieci Web z kodem, ale nie jest buforowana.

## <a name="see-also"></a>Zobacz także
- [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)