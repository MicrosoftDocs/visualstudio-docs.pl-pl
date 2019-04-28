---
title: '&lt;postAction&gt; — element (Office development w programie Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53cf47ef9a78ebb54c377e19b4f7fbad444bbfcd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976535"
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

### <a name="entrypoint"></a>entryPoint
 Opcjonalna. Rola `entryPoint` element `vstav3` przestrzeń nazw została zdefiniowana w [ &#60;punkty wejścia&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
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
