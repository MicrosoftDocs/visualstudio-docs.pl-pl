---
title: 'CA2103: Przejrzyj zabezpieczenia imperatywne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2792f1cccad26fe5bb073af800a2fcf0ebcb4b4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232985"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Przejrzyj zabezpieczenia imperatywne

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda używa imperatywnych zabezpieczeń i może konstruować uprawnienia za pomocą informacji o stanie lub wartości zwrotnych, które można zmienić, dopóki żądanie jest aktywne.

## <a name="rule-description"></a>Opis reguły
Zabezpieczenia bezwzględne wykorzystują zarządzane obiekty do określania uprawnień i akcji zabezpieczeń podczas wykonywania kodu w porównaniu z zabezpieczeniami deklaratywnymi, które używają atrybutów do przechowywania uprawnień i akcji w metadanych. Zasadnicze zabezpieczenia są bardzo elastyczne, ponieważ można ustawić stan obiektu uprawnień i wybrać akcje zabezpieczeń przy użyciu informacji, które nie są dostępne do czasu uruchomienia. Ze względu na to elastyczność wiąże się z ryzykiem, że informacje o środowisku uruchomieniowym, które są używane do określenia stanu uprawnienia, nie pozostaną bez zmian, dopóki ta akcja jest aktywna.

Należy używać zabezpieczeń deklaracyjnych wszędzie, gdzie to możliwe. Wymagania deklaracyjne są łatwiejsze do zrozumienia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Zapoznaj się z niezależnymi wymaganiami dotyczącymi zabezpieczeń, aby upewnić się, że stan uprawnienia nie polega na informacjach, które mogą ulec zmianie, o ile uprawnienia są używane.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli uprawnienie nie polega na zmienianiu danych, można bezpiecznie pominąć ostrzeżenie z tej reguły. Jednak lepiej jest zmienić pierwotne zapotrzebowanie na jego deklaratywny odpowiednik.

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Dane i modelowanie](/dotnet/framework/data/index)