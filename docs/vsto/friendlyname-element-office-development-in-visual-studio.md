---
description: Element FriendlyName przestrzeni nazw vstov4 przechowuje nazwę, która pojawia się na liście zainstalowanych programów.
title: '&lt;FriendlyName, &gt; element (Programowanie Office w Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: adcf46a2c232176026181283549c0c59fc713603
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223449"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;FriendlyName, &gt; element (Programowanie Office w Visual Studio)
  `friendlyName`Element `vstov4` przestrzeni nazw przechowuje nazwę, która pojawia się na liście zainstalowanych programów.

## <a name="syntax"></a>Składnia

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `friendlyName`Element znajduje się w `vstov4` przestrzeni nazw. Wartość zostanie wyświetlona na liście zainstalowanych programów na komputerze, a w oknie dialogowym Dodatki programu VSTO (COM) Microsoft Office aplikacji.

 `friendlyName`Element nie ma atrybutów ani elementów podrzędnych.

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `friendlyName` element w rozwiązaniu na poziomie aplikacji wdrożonym przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
