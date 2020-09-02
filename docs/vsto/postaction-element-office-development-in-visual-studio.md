---
title: '&lt;postAction — &gt; element (Programowanie Office w Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: 149aa0cf8543f5b5b1b5ada18a8b2f0e58f063d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546942"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction — &gt; element (Programowanie Office w Visual Studio)
  `postAction`Element `vstav3` przestrzeni nazw zawiera `entrypoint` elementy i wszystkie `postActionData` elementy, które są skojarzone z akcjami po wdrożeniu, które są uruchamiane po zainstalowaniu rozwiązań pakietu Office.

## <a name="syntax"></a>Składnia

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `postAction`Element jest opcjonalny i znajduje się w `vstav3` przestrzeni nazw. Istnieje jeden `postAction` element zdefiniowany w manifeście aplikacji dla każdej akcji wykonywanej po wdrożeniu.

 `postAction`Element nie ma żadnych atrybutów.

 `postAction` ma następujące elementy.

### <a name="entrypoint"></a>Punkt
 Opcjonalny. Rola `entryPoint` elementu w `vstav3` przestrzeni nazw jest definiowana w [&#60;punktach wejścia&#62; elementu &#40;programowanie Office w&#41;programu Visual Studio ](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 Opcjonalny. Rola `postActionData` elementu w `vstav3` przestrzeni nazw jest definiowana w [&#60;postActionData&#62; elementu &#40;programowanie Office w&#41;programu Visual Studio ](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Przykład akcji wykonywanej po wdrożeniu

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `postAction` element w manifeście aplikacji dla rozwiązania pakietu Office wdrożonego za pomocą programu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
