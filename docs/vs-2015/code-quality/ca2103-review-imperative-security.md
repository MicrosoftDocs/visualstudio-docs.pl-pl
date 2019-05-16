---
title: 'CA2103: Przejrzyj zabezpieczenia imperatywne | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b8b3067d5c8ab8204d6ad723315c400e7b27552
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694928"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Przejrzyj zabezpieczenia imperatywne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="see-also"></a>Zobacz też
 [Wytyczne dotyczące bezpiecznego programowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [dane i modelowanie](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
