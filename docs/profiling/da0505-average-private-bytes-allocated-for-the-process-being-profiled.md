---
title: 'DA0505: Średnie bajty prywatne przydzielone do profilowanego procesu | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b905b0de69110f5f7cd684deb6fe6c5955bb4b0c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777406"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Średnie bajty prywatne przydzielone dla procesu poddawanego profilowaniu

|||
|-|-|
|Identyfikator reguły|DA0505|
|Kategoria|Zarządzanie zasobami|
|Metoda profilowania|Wszystkie|
|Komunikat|Informacje te zostały zebrane wyłącznie w celu uzyskania informacji. Licznik Bajtów prywatnych proces mierzy pamięć wirtualną przydzieloną przez proces profilowania. Zgłoszona wartość jest średnią obliczoną we wszystkich interwałach pomiarowych.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat informuje o średniej ilości pamięci wirtualnej, która jest obecnie alokowana w bajtach (bajtach prywatnych). Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, który jest dostępny tylko przez wątki uruchomione wewnątrz procesu.

 W przypadku procesów 32-bitowych uruchomionych na komputerze 32-bitowym górna granica prywatnej części przestrzeni adresowej procesu wynosi 2 GB. Za pomocą przełącznika [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini, 32-bitowe procesy mogą uzyskać do 3 GB pamięci wirtualnej. Proces 32-bitowy uruchomiony na komputerze 64-bitowym może uzyskać do 4 GB prywatnej pamięci wirtualnej.

 Proces 64-bitowy uruchomiony na komputerze 64-bitowym może uzyskać do 8 TB prywatnej pamięci wirtualnej.

 Zgłoszona wartość jest średnią we wszystkich interwałach pomiaru, w których profilowany proces był aktywny.

 Aby uzyskać więcej informacji na temat przestrzeni adresowych procesu, zobacz [Wirtualna przestrzeń adresowa](/windows/win32/memory/virtual-address-space) w dokumentacji zarządzania pamięcią systemu Windows.

## <a name="how-to-use-rule-data"></a>Jak korzystać z danych reguły
 Użyj zgłoszonej wartości, aby porównać wydajność różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w różnych scenariuszach profilowania.
