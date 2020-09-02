---
title: '&lt;Update — &gt; element (Programowanie Office w Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: 241bddb8c79a01bb1ba6921486a4dc46d99940cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537387"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Update — &gt; element (Programowanie Office w Visual Studio)
  `update`Element Określa interwał, w którym rozwiązanie będzie sprawdzać dostępność aktualizacji.

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

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `update`Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw.

 `update`Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Wymagany. Ustaw wartość włączone na jedną z następujących wartości:<br /><br /> -   **wartość true** , aby sprawdzić dostępność aktualizacji.<br />-   **wartość false** uniemożliwia sprawdzenie dostępności aktualizacji.|

 `update`Element ma następujące elementy podrzędne.

### <a name="expiration"></a>datę
 `expiration`Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw. Ten element Określa interwał sprawdzania dostępności aktualizacji przez rozwiązanie.

 `expiration`Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`maximumAge`| Wymagany. Ustaw tę wartość jako liczbę całkowitą.|
|`unit`|Wymagany. Ustaw `unit` jedną z następujących wartości:<br /><br /> -   **liczb**<br />-   **dni**<br />-   **tygodni**|

## <a name="example-of-always-checking-for-updates"></a>Przykład zawsze sprawdzaj, czy są aktualizacje

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `update` element, który jest ustawiony na zawsze sprawdzać dostępność aktualizacji w rozwiązaniach pakietu Office.

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Przykład ustawienia domyślnego interwału aktualizacji

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `update` element w manifeście aplikacji dla rozwiązań pakietu Office. Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Zobacz też

- [Wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
