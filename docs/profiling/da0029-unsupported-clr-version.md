---
title: DA0029 — nieobsługiwana wersja środowiska CLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 18cf60804e65f2cb67f74c5739a879a633043778
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936616"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: nieobsługiwana wersja środowiska CLR

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0029|
|Kategoria|Użycie narzędzia profilowania|
|Metoda profilowania|Profilowanie z wiersza polecenia|
|Komunikat|Podczas zbierania wykryto nieobsługiwaną wersję środowiska CLR. Zarządzane symbole mogą nie zostać poprawnie rozwiązane.|
|Typ reguły|Zawartych.|

## <a name="cause"></a>Przyczyna
 Podjęto próbę profilowania aplikacji, która używa programu [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] , która nie jest obsługiwana przez narzędzia profilowania.

## <a name="rule-description"></a>Opis reguły
 To ostrzeżenie występuje, ponieważ narzędzia profilowania nie będą mogły rozpoznać symboli dla kodu zarządzanego działającego w aplikacji. Narzędzia profilowania nie mogą rozpoznać symboli kodu zarządzanego dla aplikacji, na których działa program [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Brak.
