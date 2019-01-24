---
title: 'DA0506: Maksymalna liczba bajtów prywatnych alokowanych dla PROFILOWANEGO procesu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97d1cacccc2fdd6abbd13aace1de71b28975779e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767492"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Maksymalna liczba bajtów prywatnych alokowanych dla PROFILOWANEGO procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|DA0506|  
|Category|Resource Monitoring|  
| Metoda profilowania | Wszystkie |  
| Komunikat | Te dane zostały zebrane wyłącznie w celach informacyjnych. Licznik bajtów prywatnych procesu mierzy pamięć wirtualną alokowaną przez profilowany proces. Zgłaszana wartość to maksimum zaobserwowane we wszystkich interwałach pomiarowych. |  
| Typ reguły | Informacji |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty maksymalną ilość pamięci wirtualnej, która w bajtach (bajty prywatne) aktualnie przydzielonej przez proces. Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, który może zostać oceniony jedynie przez działający proces wątki.  
  
 Dla 32-bitowych procesów uruchomionych na komputerze 32-bitowym górny limit prywatna część przestrzeni adresowej procesu wynosi 2 GB. Za pomocą [3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) przełącznika pliku Boot.ini, procesów 32-bitowych można pobrać do 3 GB pamięci wirtualnej. Proces 32-bitowy, który działa na komputerze 64-bitowym, mogą uzyskiwać maksymalnie 4 GB pamięci wirtualnej prywatny.  
  
 Proces 64-bitowy, który działa na komputerze 64-bitowym, mogą uzyskiwać do 8 TB pamięci wirtualnej prywatny.  
  
 Wartość zgłaszaną jest maksymalną we wszystkich interwałach pomiarowych, w których była aktywna PROFILOWANEGO procesu.  
  
 Aby uzyskać więcej informacji na temat procesu przestrzeni adresowych zobacz [wirtualną przestrzenią adresów](http://go.microsoft.com/fwlink/?LinkId=177832) w dokumentacji programu Windows zarządzania pamięcią.  
  
## <a name="how-to-use-rule-data"></a>Sposób użycia danych reguły  
 Aby porównać wydajność różnych wersji lub kompilacjach programu lub aby zrozumieć wydajność aplikacji w różnych scenariuszach profilowania, należy użyć podanej wartości.  
  
 Maksymalna wartość Prywatne bajty procesu, który zbliża się do limitu architektury dla rozmiar, jaki można powiększać przestrzeni adresowej procesu może prowadzić do poza wyjątki pamięci. Aby uzyskać więcej informacji, zobacz [badanie problemów z pamięcią](http://go.microsoft.com/fwlink/?LinkID=177833) w MSDN Magazine.
