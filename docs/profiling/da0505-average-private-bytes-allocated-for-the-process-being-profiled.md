---
title: 'DA0505: Średnia liczba bajtów prywatnych przydzielono dla profilowanego procesu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cff41d3ff03efd70eb876531a2d7b8602d3f8796
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72910169"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Średnie bajty prywatne przydzielone dla procesu poddawanego profilowaniu

|||
|-|-|
|Identyfikator reguły|DA0505|
|Kategoria|Zarządzanie zasobami|
|Metoda profilowania|Wszystkie|
|Komunikat|Te informacje zostały zebrane tylko w celu uzyskania informacji. Licznik bajtów prywatnych procesu mierzy pamięć wirtualną przydzieloną przez proces profilowania. Raportowana wartość to średnia obliczona dla wszystkich interwałów pomiarowych.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat przedstawia średnią ilość pamięci wirtualnej, która jest aktualnie przypisana w bajtach (bajty prywatne). Bajty prywatne reprezentują lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, do którego można uzyskać dostęp tylko przez wątki działające w procesie.

 W przypadku procesów 32-bitowych uruchomionych na komputerze 32-bitowym górny limit prywatnej części przestrzeni adresowej procesu wynosi 2 GB. Za pomocą przełącznika pliku Boot. ini programu [/3gb](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) procesy 32-bitowe mogą uzyskać do 3 GB pamięci wirtualnej. Proces 32-bitowy, który jest uruchomiony na komputerze 64-bitowym, może uzyskać do 4 GB prywatnej pamięci wirtualnej.

 Proces 64-bitowy, który jest uruchomiony na komputerze 64-bitowym, może uzyskać do 8 TB prywatnej pamięci wirtualnej.

 Raportowana wartość jest wartością średnią dla wszystkich interwałów pomiarowych, w przypadku których proces profilowany jest aktywny.

 Aby uzyskać więcej informacji na temat przestrzeni adresów procesów, zobacz [wirtualna przestrzeń adresowa](/windows/win32/memory/virtual-address-space) w dokumentacji zarządzania pamięcią systemu Windows.

## <a name="how-to-use-rule-data"></a>Jak używać danych reguł
 Wartość raportowana służy do porównywania wydajności różnych wersji lub kompilacji programu lub do zrozumienia wydajności aplikacji w różnych scenariuszach profilowania.