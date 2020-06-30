---
title: '&lt;Description — &gt; element (Programowanie Office w Visual Studio)'
titleSuffix: ''
ms.custom: secdec18
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: 4c8b54f8ccf2181a053ae5d2fe221b49840cd72c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520270"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Description — &gt; element (Programowanie Office w Visual Studio)
  `description`Element `vstov4` przestrzeni nazw przechowuje opis rozwiązania pakietu Office, które pojawia się w oknie dialogowym dodatki COM Microsoft Office aplikacji.

## <a name="syntax"></a>Składnia

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 Opcjonalny. `description`Element znajduje się w `vstov4` przestrzeni nazw. Zawiera opis dodatku, który pojawia się w oknie dialogowym Dodatki COM Microsoft Office aplikacji.

 `description`Element nie ma atrybutów ani elementów.

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `description` element rozwiązania na poziomie aplikacji wdrożonego za pomocą programu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)