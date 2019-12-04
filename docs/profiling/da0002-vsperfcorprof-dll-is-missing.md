---
title: 'DA0002: Brak pliku VSPerfCorProf. dll brakuje | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f768a35e7c50ec55867ae49901718063ca39bd0b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777754"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: brakuje VSPerfCorProf.dll

|||
|-|-|
|Identyfikator zasady|DA0002|
|Kategoria|Użycie narzędzia profilowania|
|Metody profilowania|Profilowanie przy użyciu narzędzi wiersza polecenia VSPerfCmd i VSPerfASPNETCmd|
|Komunikat|Wydaje się, że plik został zebrany bez prawidłowego ustawienia zmiennych środowiskowych za pomocą *VSPerfCLREnv. cmd*. Symbole dla zarządzanych plików binarnych mogą nie być rozpoznawane.|
|Typ reguły|Informacje programu|

## <a name="cause"></a>Przyczyna
 Profiler nie mógł znaleźć *Brak pliku VSPerfCorProf. dll* podczas przebiegu profilowania. To ostrzeżenie występuje, gdy narzędzia wiersza polecenia dla kolekcji danych profilera są używane bez użycia narzędzia *VSPerfCLREnv. cmd* w celu zainicjowania niezbędnych zmiennych środowiskowych. Ostrzeżenie może również być wyzwalane, jeśli inny Profiler jest uruchomiony po rozpoczęciu narzędzia profilowania.

## <a name="rule-description"></a>Opis reguły
 Określone zmienne środowiskowe muszą zostać ustawione przed uruchomieniem profilowania dla profilera w celu rozpoznania symboli w plikach binarnych .NET Framework. To ostrzeżenie sugeruje, że narzędzie *VSPerfCLREnv. cmd* nie zostało uruchomione przed zebraniem danych profilowania. Symbole dla zarządzanych plików binarnych mogą nie być rozpoznawane. Aby uzyskać więcej informacji na temat używania narzędzia profilowania z wiersza polecenia, zobacz [profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Podczas profilowania aplikacji zarządzanych przy użyciu narzędzi wiersza polecenia w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania Uruchom narzędzie wiersza polecenia [VSPerfCLREnv](../profiling/vsperfclrenv.md) przed rozpoczęciem zbierania danych.
