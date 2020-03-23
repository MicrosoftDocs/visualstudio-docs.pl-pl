---
title: 'DA0506: Maksymalna liczba bajtów prywatnych przydzielonych do profilowanego procesu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7600e65beb3035fac6d5ea58b25f6965d681f83a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779314"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Maksymalne bajty prywatne przydzielone dla procesu poddawanego profilowaniu

|||
|-|-|
|Identyfikator reguły|DA0506|
|Kategoria|Monitorowanie zasobów|
|Metoda profilowania|Wszystkie|
|Komunikat|Informacje te zostały zebrane wyłącznie w celu uzyskania informacji. Licznik Bajtów prywatnych proces mierzy pamięć wirtualną przydzieloną przez proces profilowania. Zgłoszona wartość jest maksymalną obserwowaną we wszystkich odstępach czasu pomiaru.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat informuje o maksymalnej ilości pamięci wirtualnej, która jest obecnie alokowana w bajtach (bajtach prywatnych). Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, który jest dostępny tylko przez wątki uruchomione wewnątrz procesu.

 W przypadku procesów 32-bitowych uruchomionych na komputerze 32-bitowym górna granica prywatnej części przestrzeni adresowej procesu wynosi 2 GB. Za pomocą przełącznika Boot.ini [/3 GB,](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) 32-bitowe procesy mogą uzyskać do 3 GB pamięci wirtualnej. Proces 32-bitowy uruchomiony na komputerze 64-bitowym może uzyskać do 4 GB prywatnej pamięci wirtualnej.

 Proces 64-bitowy uruchomiony na komputerze 64-bitowym może uzyskać do 8 TB prywatnej pamięci wirtualnej.

 Zgłoszona wartość jest maksymalna we wszystkich interwałach pomiaru, w których profilowany proces był aktywny.

 Aby uzyskać więcej informacji na temat przestrzeni adresowych procesu, zobacz [Wirtualna przestrzeń adresowa](/windows/win32/memory/virtual-address-space) w dokumentacji zarządzania pamięcią systemu Windows.

## <a name="how-to-use-rule-data"></a>Jak korzystać z danych reguły
 Użyj zgłoszonej wartości, aby porównać wydajność różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w różnych scenariuszach profilowania.

 Maksymalna wartość bajtów prywatnych procesu, która zbliża się do granicy architektury, jak duża przestrzeń adresowa procesu może rosnąć może prowadzić do wyjątków poza pamięcią. Aby uzyskać więcej informacji, zobacz [Badanie problemów z pamięcią](https://msdn.microsoft.com/magazine/cc163528.aspx) w magazynie MSDN.
