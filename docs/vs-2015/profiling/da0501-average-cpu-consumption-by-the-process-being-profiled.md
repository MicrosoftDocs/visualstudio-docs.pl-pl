---
title: 'DA0501: Średnie wykorzystanie CPU przez proces poddawany profilowaniu. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1462ac73e599b870f015a02998c069f7613be0ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155775"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Średnie wykorzystanie CPU przez proces poddawany profilowaniu.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA501 |  
| Kategoria | Monitorowanie zasobów |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Średnie użycie procesora przez profilowany proces. |  
| Typ reguły | Informacje |  
  
 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat przedstawia wartość procentową czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Raportowana wartość jest wartością średnią dla wszystkich interwałów pomiarowych, w przypadku których proces profilowany jest aktywny. Wartość może być większa niż 100% na komputerze z więcej niż jednym procesorem.  
  
## <a name="how-to-use-rule-data"></a>Jak używać danych reguł  
 Użyj wartości reguły, aby porównać wydajność różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w różnych scenariuszach testowych.
