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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 61c71bac86bed67750997ac225e3a17250183429
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854493"
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