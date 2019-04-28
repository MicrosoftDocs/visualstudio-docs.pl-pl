---
title: Zbieranie danych o interakcji między warstwami | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcdab1fcb776a729d00a143dfc318053b74c5cf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831505"
---
# <a name="collect-tier-interaction-data"></a>Zbieranie danych o interakcji między warstwami

Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje na temat czasu wykonania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem usług ADO.NET. Dane są zbierane tylko w przypadku wywołania funkcji synchronicznej.

**Visual Studio editions**

Obejrzeć takie dane mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Natomiast obejrzeć takie dane można wyświetlać tylko w programie Visual Studio Enterprise.

**System Windows 8 i Windows Server 2012**

Aby zebrać dane interakcji między warstwami na aplikacje pulpitu systemu Windows 8 i aplikacje systemu Windows Server 2012, należy użyć metody instrumentacji. Nie można zebrać dane interakcji między warstwami aplikacji platformy uniwersalnej systemu Windows. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Dane interakcji między warstwami można uwzględnić w wszystkich metod profilowania w innych obsługiwanych wersji systemu Windows.

**Kreator wydajności**

Ze względu na błąd Kreatora wydajności należy dodać opcji zbierania danych interakcji warstwy do uruchomienia profilowania z poziomu Eksploratora wydajności. Do węzła docelowego Eksploratora wydajności, należy dodać projekt, plik wykonywalny lub witryny sieci Web.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Aby dodać dane interakcji między warstwami do profilowania za pomocą stron właściwości sesji wydajności

1. W Eksploratorze wydajności, wybierz **właściwości** z menu kontekstowego.

2. Wybierz **interakcje warstw** strony, a następnie sprawdź **Włącz profilowanie interakcji pomiędzy warstwami** pole wyboru.

3. W Eksploratorze wydajności wybierz **cele** węzła, a następnie określ project, plik wykonywalny lub witryny sieci web, które powinny być profilowane.

## <a name="see-also"></a>Zobacz także

[Widok interakcji warstwowych](../profiling/tier-interactions-view.md)