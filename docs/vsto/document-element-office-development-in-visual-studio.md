---
title: '&lt;dokument&gt; — element (Office development w programie Visual Studio)'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36d822d60d1a28d48f660f6d358b75bf4a913048
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866389"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;dokument&gt; — element (Office development w programie Visual Studio)
  `document` Elementu `vstov4` przestrzeni nazw są przechowywane informacje dotyczące dostosowywania przypadku dostosowań na poziomie dokumentu.

## <a name="syntax"></a>Składnia

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 Wymagane tylko w przypadku dostosowań na poziomie dokumentu. `document` Element znajduje się w `vstov4` przestrzeni nazw. `document` Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`solutionId`|Wymagana. Identyfikator GUID używany przez Visual Studio Tools for Office runtime do jednoznacznego identyfikowania to rozwiązanie na poziomie dokumentu. Ta wartość jest przechowywana jako _AssemblyLocation niestandardową właściwość dokumentu. Aby uzyskać więcej informacji, zobacz [właściwości niestandardowego dokumentu ― omówienie](../vsto/custom-document-properties-overview.md).|

 `document` nie ma elementów podrzędnych.

## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `document` elementu w poziomie dokumentu rozwiązań pakietu Office, wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)