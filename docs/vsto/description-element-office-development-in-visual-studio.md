---
title: '&lt;Description — &gt; element (Programowanie Office w Visual Studio)'
description: Dowiedz się, że element Description w przestrzeni nazw vstov4 przechowuje opis rozwiązania pakietu Office, które pojawia się w oknie dialogowym Dodatki COM.
titleSuffix: ''
ms.custom: secdec18, SEO-VS-2020
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
ms.openlocfilehash: 377599e770a93faca9e283ec543091508b773bc7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846236"
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

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)