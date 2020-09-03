---
title: 'DA0502: maksymalne użycie procesora przez profilowany proces | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a47a9c5964ccf15d2c609233eb600f39bc3ad2d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205936"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Maksymalne użycie procesora przez profilowany proces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0502 |  
| Kategoria | Monitorowanie zasobów |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Ta reguła służy tylko do celów informacyjnych. \\Licznik czas procesora (%) mierzy użycie procesora przez proces profilowania. Raportowana wartość jest maksimum zaobserwowane we wszystkich interwałach pomiarowych. |  
| Typ reguły | Informacje |  
  
 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat zgłasza maksymalny procent czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Raportowana wartość jest wartością maksymalną raportowaną we wszystkich interwałach pomiarowych, w których proces profilowany był aktywny. Wartość procentowa może być większa niż 100% na komputerze z więcej niż jednym procesorem.  
  
## <a name="how-to-use-the-rule-data"></a>Jak korzystać z danych reguły  
 Wartość reguły służy do porównywania wydajności różnych wersji lub kompilacji programu lub do zrozumienia wydajności aplikacji w różnych scenariuszach profilowania.
