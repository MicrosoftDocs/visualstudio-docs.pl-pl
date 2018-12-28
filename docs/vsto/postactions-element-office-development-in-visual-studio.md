---
title: '&lt;postactions —&gt; — element (Office development w programie Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c2036cf0d632fcf545dfde0ec4c43caa788a85ed
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804815"
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postactions —&gt; — element (Office development w programie Visual Studio)
  `postActions` Elementu `vstav3` przestrzeń nazw zawiera wszystkie `postAction` elementy, które opisują działania po wdrożeniu, uruchamianych po zainstalowaniu rozwiązania dla pakietu Office.

## <a name="syntax"></a>Składnia

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `postActions` Elementu jest opcjonalna i jest on `vstav3` przestrzeni nazw. Jest tylko jedna `postActions` elementu zdefiniowanego w manifeście aplikacji.

 `postActions` Element nie ma żadnych atrybutów.

 `postActions` ma następujący element.

### <a name="postaction"></a>postAction
 Opcjonalna. Rola `postAction` element `vstav3` przestrzeń nazw została zdefiniowana w [ &#60;postAction&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Przykład akcję powdrożeniową

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `postActions` elementu w manifeście aplikacji dla rozwiązań pakietu Office, wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:postActions>
  <vstav3:postAction>
    <vstav3:entryPoint
      class="PostDeploymentAction.PostDeploymentActionSample">
      <assemblyIdentity
        name="PostDeploymentAction"
        version="1.0.0.0"
        language="neutral"
        processorArchitecture="msil" />
    </vstav3:entryPoint>
    <vstav3:postActionData>
    </vstav3:postActionData>
  </vstav3:postAction>
</vstav3:postActions>
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
