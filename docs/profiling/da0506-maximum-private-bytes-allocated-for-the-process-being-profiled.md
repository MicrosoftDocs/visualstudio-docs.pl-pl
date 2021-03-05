---
description: Ten komunikat przedstawia maksymalną ilość pamięci wirtualnej, która jest aktualnie przypisana w bajtach (bajty prywatne).
title: DA0506 — Maksymalna liczba bajtów prywatnych przydzielono dla profilowanego procesu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a796dd962485e5569ec09b07b881a8bb183b6e9d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223644"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Maksymalna liczba bajtów prywatnych przydzielonych dla profilowanego procesu

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0506|
|Kategoria|Monitorowanie zasobów|
|Metoda profilowania|Wszystko|
|Komunikat|Te informacje zostały zebrane tylko w celu uzyskania informacji. Licznik bajtów prywatnych procesu mierzy pamięć wirtualną przydzieloną przez proces profilowania. Raportowana wartość jest maksimum zaobserwowane we wszystkich interwałach pomiarowych.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat przedstawia maksymalną ilość pamięci wirtualnej, która jest aktualnie przypisana w bajtach (bajty prywatne). Bajty prywatne reprezentują lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, do którego można uzyskać dostęp tylko przez wątki działające w procesie.

 W przypadku procesów 32-bitowych uruchomionych na komputerze 32-bitowym górny limit prywatnej części przestrzeni adresowej procesu wynosi 2 GB. Korzystając z przełącznika [/3 gb](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini, procesy 32-bitowe mogą uzyskać do 3 GB pamięci wirtualnej. Proces 32-bitowy, który jest uruchomiony na komputerze 64-bitowym, może uzyskać do 4 GB prywatnej pamięci wirtualnej.

 Proces 64-bitowy, który jest uruchomiony na komputerze 64-bitowym, może uzyskać do 8 TB prywatnej pamięci wirtualnej.

 Raportowana wartość jest wartością maksymalną dla wszystkich interwałów pomiarowych, w przypadku których proces profilowany był aktywny.

 Aby uzyskać więcej informacji na temat przestrzeni adresów procesów, zobacz [wirtualna przestrzeń adresowa](/windows/win32/memory/virtual-address-space) w dokumentacji zarządzania pamięcią systemu Windows.

## <a name="how-to-use-rule-data"></a>Jak używać danych reguł
 Wartość raportowana służy do porównywania wydajności różnych wersji lub kompilacji programu lub do zrozumienia wydajności aplikacji w różnych scenariuszach profilowania.

 Maksymalna wartość bajtów prywatnych procesów, która zbliża się do limitu architektury przestrzeni adresowej procesu może zwiększyć się do wyjątków pamięci. Aby uzyskać więcej informacji, zobacz temat [Badanie problemów z pamięcią](/archive/msdn-magazine/2006/november/clr-inside-out-investigating-memory-issues) w magazynie MSDN.
