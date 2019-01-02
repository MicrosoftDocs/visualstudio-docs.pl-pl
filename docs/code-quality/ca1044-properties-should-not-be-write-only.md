---
title: 'CA1044: Właściwości nie powinny być tylko do zapisu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e9d543c915cecbaa4f37a694786e80876bdf06cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959095"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Właściwości nie powinny być tylko do zapisu

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Właściwość publiczna lub chroniona ma metody dostępu set, ale nie ma ona metody dostępu get.

## <a name="rule-description"></a>Opis reguły
 Metody dostępu zapewniają dostęp do odczytu do właściwości i metody dostępu set zapewniają dostęp do zapisu. Chociaż posiadanie właściwości tylko do odczytu jest dopuszczalne i często konieczne, wytyczne projektowania zabraniają używania właściwości tylko do zapisu. Jest to spowodowane umożliwienie użytkownikowi ustawienia wartości, a następnie uniemożliwianie przeglądania wartości nie zapewnia żadnych zabezpieczeń. Poza tym bez dostępu do odczytu nie można przeglądać stanu obiektów udostępnionych, co ogranicza ich przydatność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać do właściwości metody dostępu get. Alternatywnie Jeśli konieczne jest zachowanie właściwości tylko do zapisu, należy rozważyć przekonwertowanie tej właściwości na metodę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Zalecane jest, pomija ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie `BadClassWithWriteOnlyProperty` jest typem z właściwością tylko do zapisu. `GoodClassWithReadWriteProperty` zawiera kod poprawiony.

 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]