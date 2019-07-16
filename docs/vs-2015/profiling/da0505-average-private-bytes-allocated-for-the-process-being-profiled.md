---
title: 'DA0505: Średnia liczba bajtów prywatnych alokowanych dla PROFILOWANEGO procesu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fde4228538a26a4601dc7eb5638a4b803dafbacb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205908"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Średnia liczba bajtów prywatnych przydzielonych dla profilowanego procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0505 |  
|Category|Resource Management|  
| Metoda profilowania | Wszystkie |  
| Komunikat | Te dane zostały zebrane wyłącznie w celach informacyjnych. Licznik bajtów prywatnych procesu mierzy pamięć wirtualną alokowaną przez profilowany proces. Zgłaszana wartość to średnia obliczona dla wszystkich interwałów pomiarowych. |  
| Typ reguły | Informacji |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty średniej ilości pamięci wirtualnej, która w bajtach (bajty prywatne) aktualnie przydzielonej przez proces. Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, który może zostać oceniony jedynie przez działający proces wątki.  
  
 Dla 32-bitowych procesów uruchomionych na komputerze 32-bitowym górny limit prywatna część przestrzeni adresowej procesu wynosi 2 GB. Za pomocą [3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) przełącznika pliku Boot.ini, procesów 32-bitowych można pobrać do 3 GB pamięci wirtualnej. Proces 32-bitowy, który działa na komputerze 64-bitowym, mogą uzyskiwać maksymalnie 4 GB pamięci wirtualnej prywatny.  
  
 Proces 64-bitowy, który działa na komputerze 64-bitowym, mogą uzyskiwać do 8 TB pamięci wirtualnej prywatny.  
  
 Wartość zgłaszaną jest średnią we wszystkich interwałach pomiarowych, w których była aktywna PROFILOWANEGO procesu.  
  
 Aby uzyskać więcej informacji na temat procesu przestrzeni adresowych zobacz [wirtualną przestrzenią adresów](http://go.microsoft.com/fwlink/?LinkId=177832) w dokumentacji programu Windows zarządzania pamięcią.  
  
## <a name="how-to-use-rule-data"></a>Sposób użycia danych reguły  
 Aby porównać wydajność różnych wersji lub kompilacjach programu lub aby zrozumieć wydajność aplikacji w różnych scenariuszach profilowania, należy użyć podanej wartości.
