---
title: '&lt;Aktualizuj&gt; — element (Office development w programie Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 461fae79e3af346d64017166b6dae3ace67599e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967536"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Aktualizuj&gt; — element (Office development w programie Visual Studio)
  `update` Element Określa interwał, w którym rozwiązanie będzie sprawdzać, które aktualizacje.

## <a name="syntax"></a>Składnia

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `update` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw.

 `update` Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Wymagana. Dla węzła enabled Ustaw na jedną z następujących wartości:<br /><br /> -   **wartość true,** pod kątem aktualizacji.<br />-   **FALSE** zapobiegające sprawdzania dostępności aktualizacji.|

 `update` Element ma następujących elementów podrzędnych.

### <a name="expiration"></a>wygaśnięcie
 `expiration` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw. Ten element Określa interwał, z jaką rozwiązanie będzie sprawdzać dostępność aktualizacji.

 `expiration` Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`maximumAge`| Wymagana. Ustaw to na liczbę całkowitą.|
|`unit`|Wymagana. Ustaw `unit` do jednej z następujących wartości:<br /><br /> -   **godz.**<br />-   **dni**<br />-   **tyg.**|

## <a name="example-of-always-checking-for-updates"></a>Przykład zawsze sprawdzania dostępności aktualizacji

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `update` element, który jest ustawiony na Zawsze sprawdzaj dostępność aktualizacji w rozwiązaniach pakietu Office.

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Przykładowa konfiguracja domyślny interwał aktualizacji

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `update` elementu w manifeście aplikacji dla rozwiązań pakietu Office. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Zobacz także

- [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
