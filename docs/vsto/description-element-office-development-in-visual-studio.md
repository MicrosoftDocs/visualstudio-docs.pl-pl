---
title: '&lt;Opis&gt; — element (Office development w programie Visual Studio)'
titleSuffix: ''
ms.custom: secdec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ede5ac920c1d40402504544a13f8a00905b82e80
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871328"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Opis&gt; — element (Office development w programie Visual Studio)
  `description` Elementu `vstov4` przestrzeni nazw przechowuje opis rozwiązania pakietu Office, który pojawia się w oknie dialogowym dodatków COM aplikacji pakietu Microsoft Office.

## <a name="syntax"></a>Składnia

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 Opcjonalna. `description` Element znajduje się w `vstov4` przestrzeni nazw. Zawiera opis dodatku, który pojawia się w oknie dialogowym dodatków COM aplikacji pakietu Microsoft Office.

 `description` Element nie ma atrybutów lub elementów.

## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `description` elementu dla rozwiązań pakietu dodatku poziomu aplikacji wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)