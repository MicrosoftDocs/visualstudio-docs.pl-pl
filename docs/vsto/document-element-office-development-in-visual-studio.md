---
title: '&lt;Document — &gt; element (Programowanie Office w Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e92c17d71b1c0959cb1918ce6fbad0e2cd44d5ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949834"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;Document — &gt; element (Programowanie Office w Visual Studio)
  `document`Element `vstov4` przestrzeni nazw przechowuje informacje specyficzne dla dostosowywania dla dostosowań na poziomie dokumentu.

## <a name="syntax"></a>Składnia

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 Wymagane tylko w przypadku dostosowań na poziomie dokumentu. `document`Element znajduje się w `vstov4` przestrzeni nazw. `document`Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`solutionId`|Wymagane. Identyfikator GUID używany przez Visual Studio Tools dla środowiska uruchomieniowego pakietu Office w celu jednoznacznego zidentyfikowania rozwiązania na poziomie dokumentu. Ta wartość jest przechowywana jako _AssemblyLocation Właściwość dokumentu niestandardowego. Aby uzyskać więcej informacji, zobacz [niestandardowe właściwości dokumentu — Omówienie](../vsto/custom-document-properties-overview.md).|

 `document` nie ma elementów podrzędnych.

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `document` element w rozwiązaniu pakietu Office na poziomie dokumentu wdrożonym przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)