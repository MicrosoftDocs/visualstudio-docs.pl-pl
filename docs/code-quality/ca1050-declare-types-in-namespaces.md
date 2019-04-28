---
title: 'CA1050: Deklaruj typy w przestrzeniach nazw'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8cac669b96f362d6da73e3eb2f373137c3d9bdd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778521"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Deklaruj typy w przestrzeniach nazw

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony jest zdefiniowana poza zakresem o nazwie przestrzeni nazw.

## <a name="rule-description"></a>Opis reguły
 Typy są deklarowane w przestrzeni nazw, aby zapobiec kolizjom nazw oraz jako sposób organizowania typów powiązanych w hierarchii obiektów. Typy, które wykraczają poza dowolnego obszaru nazw, o nazwie znajdują się w globalnej przestrzeni nazw, który nie można się odwoływać w kodzie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy umieścić w przestrzeni nazw typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Mimo, że masz nigdy nie Pomijaj ostrzeżeń dla tej reguły, jest bezpieczne to zrobić, gdy zestaw nigdy nie będzie używany wraz z innymi zestawami.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, biblioteki, która ma typ niepoprawnie zadeklarowanej na zewnątrz przestrzeni nazw i typ, który ma taką samą nazwę, zadeklarowany w przestrzeni nazw.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Przykład
 Następująca aplikacja używa biblioteki, która została zdefiniowana wcześniej. Należy pamiętać, czy typ, który jest zadeklarowana poza przestrzeni nazw jest tworzone, gdy nazwa `Test` nie jest kwalifikowana przez obszar nazw. Należy zauważyć, że dostęp do `Test` wpisać `Goodspace`, wymagane jest podanie nazwy przestrzeni nazw.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]