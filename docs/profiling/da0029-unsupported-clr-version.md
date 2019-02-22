---
title: 'DA0029: Nieobsługiwana wersja środowiska CLR | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3855b8975684b088b2838a866db36e6ec19e665
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635543"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nieobsługiwana wersja środowiska CLR

|||
|-|-|
|Identyfikator reguły|DA0029|
|Kategoria|Użycie narzędzia profilowania|
|Metoda profilowania|Profilowanie z wiersza polecenia|
|Komunikat|Podczas zbierania Wykryto nieobsługiwaną wersję środowiska CLR. Symbole zarządzane mogą nie być rozpoznawane poprawnie.|
|Typ reguły|Informacje.|

## <a name="cause"></a>Przyczyna
 Chcesz profilować aplikację, która używa [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] nie jest obsługiwana przez narzędzia profilowania.

## <a name="rule-description"></a>Opis reguły
 To ostrzeżenie występuje, ponieważ narzędzia profilowania nie będzie można rozwiązać symbole dla kodu zarządzanego w aplikacji. Narzędzia profilowania nie można rozpoznać symbole kodu zarządzanego dla aplikacji, które są uruchomione [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Brak.