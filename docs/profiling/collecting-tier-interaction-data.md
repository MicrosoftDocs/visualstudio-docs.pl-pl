---
title: Zbieranie danych o interakcji warstwy | Dokumenty firmy Microsoft
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e01259fdd23e60a1408addc10a6af3a12479c9f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772821"
---
# <a name="collect-tier-interaction-data"></a>Zbieranie danych o interakcji między warstwami

Profilowanie interakcji warstwy zawiera dodatkowe informacje na temat czasów wykonywania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem usług ADO.NET. Dane są zbierane tylko dla wywołań funkcji synchronicznych.

**Wersje programu Visual Studio**

Dane profilowania interakcji warstwy mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji warstwy można wyświetlać tylko w programie Visual Studio Enterprise.

**Windows 8 i Windows Server 2012**

Aby zbierać dane interakcji warstwy w aplikacjach klasycznych systemu Windows 8 i aplikacjach systemu Windows Server 2012, należy użyć metody instrumentacji. Nie można zbierać danych interakcji warstwy dla aplikacji platformy uniwersalnej systemu Windows. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Dane interakcji warstwy można uwzględnić we wszystkich metodach profilowania w innej obsługiwanej wersji systemu Windows.

**Kreator Wydajności**

Z powodu błędu w Kreatorze wydajności należy dodać opcję zbierania danych interakcji warstwy do profilowania uruchamianego z Eksploratora wydajności. Należy również dodać projekt, plik wykonywalny lub witrynę sieci Web do węzła docelowego Eksploratora wydajności.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Aby dodać dane interakcji warstwy do profilowania uruchamianego przy użyciu stron właściwości sesji wydajności

1. W Eksploratorze wydajności wybierz polecenie **Właściwości** z menu kontekstowego.

2. Wybierz stronę **Interakcje warstwy,** a następnie zaznacz pole wyboru **Włącz profilowanie interakcji warstwy.**

3. W Eksploratorze wydajności wybierz węzeł **Cele,** a następnie określ projekt, plik wykonywalny lub witrynę sieci Web, którą chcesz profilować.

## <a name="see-also"></a>Zobacz też

[Widok interakcji warstwy](../profiling/tier-interactions-view.md)
