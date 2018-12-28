---
title: '&lt;postAction&gt; — element (Office development w programie Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34ebc9595b8b66ac4d81f5a7adef86a14b4d2a58
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802164"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; — element (Office development w programie Visual Studio)
  `postAction` Elementu `vstav3` przestrzeń nazw zawiera `entrypoint` elementy i wszystkie `postActionData` elementy, które są skojarzone z akcji po wdrożeniu, uruchamianych po zainstalowaniu rozwiązania dla pakietu Office.

## <a name="syntax"></a>Składnia

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `postAction` Elementu jest opcjonalna i jest on `vstav3` przestrzeni nazw. Istnieje `postAction` elementu zdefiniowanego w manifeście aplikacji dla każdej akcji po wdrożeniu.

 `postAction` Element nie ma żadnych atrybutów.

 `postAction` zawiera następujące elementy.

### <a name="entrypoint"></a>Punkt wejścia
 Opcjonalna. Rola `entryPoint` element `vstav3` przestrzeń nazw została zdefiniowana w [ &#60;punkty wejścia&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postactiondata —
 Opcjonalna. Rola `postActionData` element `vstav3` przestrzeń nazw została zdefiniowana w [ &#60;postactiondata —&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Przykład akcję powdrożeniową

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `postAction` elementu w manifeście aplikacji dla rozwiązań pakietu Office, który jest wdrożony za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
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
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
