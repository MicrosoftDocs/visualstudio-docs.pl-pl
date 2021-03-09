---
title: DA0002 — brak VSPerfCorProf.dll | Microsoft Docs
description: To ostrzeżenie występuje, gdy narzędzia wiersza polecenia dla kolekcji danych profilera są używane bez użycia narzędzia VSPerfCLREnv. cmd do zainicjowania niezbędnych zmiennych środowiskowych lub jeśli inny Profiler jest uruchomiony po rozpoczęciu narzędzia profilowania.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 763a28dcb2200549b13b3562ffe3ab9fa629cdc5
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466183"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: Brak biblioteki VSPerfCorProf.dll

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0002|
|Kategoria|Użycie narzędzia profilowania|
|Metody profilowania|Profilowanie przy użyciu narzędzi wiersza polecenia VSPerfCmd i VSPerfASPNETCmd|
|Komunikat|Wydaje się, że plik został zebrany bez prawidłowego ustawienia zmiennych środowiskowych za pomocą *VSPerfCLREnv. cmd*. Symbole dla zarządzanych plików binarnych mogą nie być rozpoznawane.|
|Typ reguły|Informacje|

## <a name="cause"></a>Przyczyna
 Profiler nie mógł znaleźć *VSPerfCorProf.dll* podczas przebiegu profilowania. To ostrzeżenie występuje, gdy narzędzia wiersza polecenia dla kolekcji danych profilera są używane bez użycia narzędzia *VSPerfCLREnv. cmd* w celu zainicjowania niezbędnych zmiennych środowiskowych. Ostrzeżenie może również być wyzwalane, jeśli inny Profiler jest uruchomiony po rozpoczęciu narzędzia profilowania.

## <a name="rule-description"></a>Opis reguły
 Określone zmienne środowiskowe muszą zostać ustawione przed uruchomieniem profilowania dla profilera w celu rozpoznania symboli w plikach binarnych .NET Framework. To ostrzeżenie sugeruje, że narzędzie *VSPerfCLREnv. cmd* nie zostało uruchomione przed zebraniem danych profilowania. Symbole dla zarządzanych plików binarnych mogą nie być rozpoznawane. Aby uzyskać więcej informacji na temat używania narzędzia profilowania z wiersza polecenia, zobacz [profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Podczas profilowania aplikacji zarządzanych przy użyciu narzędzi wiersza polecenia w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania należy uruchomić narzędzie wiersza polecenia [VSPerfCLREnv](../profiling/vsperfclrenv.md) przed rozpoczęciem zbierania danych.
