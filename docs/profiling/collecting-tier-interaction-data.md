---
title: Zbieranie danych o interakcji między warstwami | Microsoft Docs
description: Dowiedz się, jak zbierać informacje dotyczące profilowania warstwy dla aplikacji wielowarstwowych komunikujących się z bazami danych za pomocą usług ADO.NET Services.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e2b20a403d2c56dd239ddaf81d2a32905ca4aed5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950237"
---
# <a name="collect-tier-interaction-data"></a>Zbieranie danych o interakcji między warstwami

Profilowanie interakcji między warstwami zawiera dodatkowe informacje o czasach wykonywania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pomocą usług ADO.NET Services. Dane są zbierane tylko dla wywołań funkcji synchronicznych.

**Wersje programu Visual Studio**

Dane profilowania interakcji między warstwami można zbierać przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji między warstwami mogą być wyświetlane tylko w Visual Studio Enterprise.

**Windows 8 i Windows Server 2012**

Aby zbierać dane interakcji warstwy w aplikacjach klasycznych systemu Windows 8 i aplikacjach systemu Windows Server 2012, należy użyć metody instrumentacji. Nie można zbierać danych interakcji warstwy dla aplikacji platformy UWP. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Możesz uwzględnić dane interakcji warstwy we wszystkich metodach profilowania w innej obsługiwanej wersji systemu Windows.

**Kreator Wydajności**

Ze względu na usterkę w Kreatorze wydajności należy dodać opcję zbierania danych interakcja warstwy do przebiegu profilowania z Eksplorator wydajności. Należy również dodać projekt, plik wykonywalny lub witrynę sieci Web do węzła docelowego Eksplorator wydajności.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Aby dodać dane interakcji warstwy do przebiegu profilowania przy użyciu stron właściwości sesji wydajności

1. W Eksplorator wydajności, wybierz **Właściwości** z menu kontekstowego.

2. Wybierz stronę **interakcje warstwy** , a następnie zaznacz pole wyboru **Włącz profilowanie interakcji między warstwami** .

3. W Eksplorator wydajności Wybierz węzeł **targets** , a następnie określ projekt, plik wykonywalny lub witrynę sieci Web, którą chcesz profilować.

## <a name="see-also"></a>Zobacz też

[Widok interakcji między warstwami](../profiling/tier-interactions-view.md)
