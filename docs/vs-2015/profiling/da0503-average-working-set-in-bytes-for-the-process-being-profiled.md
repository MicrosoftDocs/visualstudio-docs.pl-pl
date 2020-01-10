---
title: 'DA0503: Średni zestaw roboczy w bajtach dla profilowanego procesu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 31d36a89473cd0c6a0b55e484fee2ce1d7045b15
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850895"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Średni rozmiar zestawu roboczego w bajtach dla procesu poddawanego profilowaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|DA0503|  
| Kategoria | Monitorowanie zasobów |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Te informacje zostały zebrane tylko w celu uzyskania informacji. Licznik zestawu roboczego procesu mierzy użycie pamięci fizycznej przez proces profilowania. Raportowana wartość to średnia obliczona dla wszystkich interwałów pomiarowych. |  
| Typ reguły | Informacje |  
  
 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat przedstawia średnią ilość pamięci fizycznej używanej aktualnie przez proces w bajtach (zestaw roboczy). Zestaw roboczy procesu przedstawia strony z przestrzeni adresowej procesu, która znajduje się obecnie w pamięci fizycznej.  
  
 Raportowana wartość obejmuje rezydentne strony z udostępnionych segmentów pamięci, do których odwołuje się proces. Udostępnione biblioteki DLL, do których odwołują się odwołania do procesów, są uwzględniane w zliczanych segmentach pamięci współdzielonej. Wartość zestawu roboczego procesu może być wyższa niż ilość pamięci wirtualnej przydzielonej przez proces z powodu udostępnionych segmentów pamięci.  
  
 Raportowana wartość jest wartością średnią dla wszystkich interwałów pomiarowych, w przypadku których proces profilowany jest aktywny.  
  
 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej, która jest aktywnie używana przez proces. Ma także wpływ na ilość pamięci fizycznej (lub pamięci RAM), która jest dostępna do uruchamiania aplikacji i rywalizacji dla tej pamięci fizycznej z innych uruchomionych procesów. Jeśli pamięć fizyczna jest ograniczona, wartość zestawu roboczego procesu to APT, tak aby system operacyjny próbował zrównoważyć użycie pamięci przez aktywne procesy przez okresowe przycinanie dość nieaktywnych stron z procesów zestawów roboczych.  
  
 Aby uzyskać więcej informacji na temat procesów zestawów roboczych, zobacz [zestaw roboczy](https://msdn.microsoft.com/library/cc441804.aspx) w dokumentacji zarządzania pamięcią systemu Windows w witrynie MSDN.  
  
## <a name="how-to-use-rule-data"></a>Jak używać danych reguł  
 Wartość reguły służy do porównywania wydajności różnych wersji lub kompilacji programu lub do zrozumienia wydajności aplikacji w różnych scenariuszach profilowania.  
  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku [Widok znaczników](../profiling/marks-view.md) danych profilowania. Znajdź **Process\Working zestawu** i kolumny **pamięć \ strony/s** . Porównaj dwie kolumny i ustal, czy istnieją określone fazy wykonywania programu, które są prawdopodobnie skojarzone ze zwiększoną aktywnością we/wy stronicowania.
