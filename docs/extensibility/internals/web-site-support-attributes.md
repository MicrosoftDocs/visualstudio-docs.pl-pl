---
title: Atrybuty pomocy technicznej witryny sieci Web | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703495"
---
# <a name="web-site-support-attributes"></a>Atrybuty pomocy technicznej dotyczącej witryn internetowych
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Projekt witryny sieci Web można rozszerzyć, aby zapewnić obsługę języków programowania sieci Web. Język musi się [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zarejestrować, aby szablony projektów mogły być wyświetlane w oknie dialogowym **Nowa witryna sieci Web** po wybraniu języka.

Przykład IronPython Studio zawiera obsługę witryny sieci Web. Przykład zawiera następujące klasy atrybutów do zarejestrowania IronPython jako języka codebehind dla nowych projektów sieci Web.

## <a name="websiteprojectattribute"></a>Atrybut WebSiteProjectAttribute
 Ten atrybut jest umieszczany w projekcie języka. Dodaje język do listy języków programowania sieci Web na liście **Język** w oknie dialogowym **Nowa witryna sieci Web.** Na przykład następujący kod dodaje IronPython do listy:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Ten atrybut ustawia również ścieżkę szablonów, aby wskazać folder szablonów. Aby uzyskać więcej informacji na temat lokalizacji folderu szablonów, zobacz [Szablony obsługi witryn sieci Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>Atrybut WebSiteProjectRelatedFilesAttribute
 Ten atrybut jest umieszczany w projekcie języka. Umożliwia projektowi witryny sieci Web zagnieżdżanie jednego typu pliku (pokrewnego) pod innym typem pliku (podstawowym) w **Eksploratorze rozwiązań**.

 Na przykład poniższy kod określa, że plik codebehind IronPython jest powiązany z plikiem .aspx. Po utworzeniu nowej strony sieci Web .aspx w rozwiązaniu witryny sieci Web IronPython generowany jest nowy plik źródłowy py i pojawia się jako węzeł podrzędny strony .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>Atrybut ProvideIntellisenseProviderAttribute
 Ten atrybut jest umieszczany w pakiecie projektu języka. Wybiera dostawcę IntelliSense dla języka.

 Na przykład poniższy kod określa, że wystąpienie PythonIntellisenseProvider, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, powinny być tworzone na żądanie w celu świadczenia usług językowych.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Implementacja IVsIntellisenseProject obsługuje odwołania i wywołuje kompilator języka, gdy strona sieci Web z kodem jest żądana, ale nie jest buforowana.

## <a name="see-also"></a>Zobacz też
- [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)
