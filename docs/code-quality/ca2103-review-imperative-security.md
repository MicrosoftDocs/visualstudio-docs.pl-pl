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
ms.openlocfilehash: 2417266da44c4af38e37eb8e0f67ac13a5a7823e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916729"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Przejrzyj zabezpieczenia imperatywne

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda używa imperatywnych zabezpieczeń i może konstruować uprawnienia za pomocą informacji o stanie lub wartości zwrotnych, które można zmienić, dopóki żądanie jest aktywne.

## <a name="rule-description"></a>Opis reguły
 Zabezpieczenia imperatywne używa obiektów zarządzanych do określania uprawnień i akcje zabezpieczeń podczas wykonywania kodu, w porównaniu do zabezpieczenia deklaratywne, który przechowuje atrybuty uprawnień i akcji w metadanych. Zabezpieczenia imperatywne jest bardzo elastyczny, ponieważ można ustawić stanu obiektu uprawnień i wybieranie akcji zabezpieczeń przy użyciu informacji, która nie jest dostępna do czasu wykonywania. Wraz z który elastyczność pochodzi ryzyko, że informacje środowiska uruchomieniowego, które można określić, że stan uprawnienia nie pozostaje bez zmian, tak długo, jak akcja jest aktywna.

 Należy używać zabezpieczeń deklaracyjnych wszędzie, gdzie to możliwe. Wymagania związane z deklaratywnych są łatwiejsze do zrozumienia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Przegląd wymagań zabezpieczenia imperatywne, aby upewnić się, czy stan uprawnienia nie polega na informacje, które można zmienić tak długo, jak uprawnienia, jest on używany.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli uprawnienia nie zależy od zmieniających się danych. Jednak zaleca się zmiany imperatywne żądanie na odpowiadającą jej deklaratywne.

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Dane i modelowanie](/dotnet/framework/data/index)