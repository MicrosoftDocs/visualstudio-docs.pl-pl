---
title: '&lt;friendlyName&gt; — element (Office development w programie Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d038e825173f95ddfe4106022c7c9924090b3a5f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873109"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt; — element (Office development w programie Visual Studio)
  `friendlyName` Elementu `vstov4` przestrzeni nazw przechowuje nazwę, która jest wyświetlana na liście zainstalowanych programów.

## <a name="syntax"></a>Składnia

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `friendlyName` Element znajduje się w `vstov4` przestrzeni nazw. Wartość jest wyświetlana na liście zainstalowanych programów na komputerze, a następnie w oknie dialogowym dodatków narzędzi VSTO dla modelu COM aplikacji pakietu Microsoft Office.

 `friendlyName` Element nie ma atrybutów lub elementów podrzędnych.

## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `friendlyName` elementu w rozwiązaniu dodatku poziomu aplikacji wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)