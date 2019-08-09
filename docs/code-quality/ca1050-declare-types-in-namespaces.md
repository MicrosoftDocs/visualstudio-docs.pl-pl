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
ms.openlocfilehash: 869ff99243349ae01c63da0a7d9e6544761cbd39
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922501"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Deklaruj typy w przestrzeniach nazw

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ publiczny lub chroniony jest zdefiniowany poza zakresem nazwanego obszaru nazw.

## <a name="rule-description"></a>Opis reguły
Typy są zadeklarowane w przestrzeniach nazw, aby zapobiec kolizjom nazw oraz jak organizować powiązane typy w hierarchii obiektów. Typy, które są poza dowolnym nazwanym obszarem nazw, znajdują się w globalnej przestrzeni nazw, do której nie można odwoływać się w kodzie

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, umieść typ w przestrzeni nazw.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Mimo że nigdy nie trzeba pominąć ostrzeżenia z tej reguły, jest to bezpieczne, gdy zestaw nigdy nie będzie używany razem z innymi zestawami.

## <a name="example"></a>Przykład
W poniższym przykładzie przedstawiono bibliotekę, która ma nieprawidłowo zadeklarowany element poza przestrzenią nazw, i typ, który ma taką samą nazwę zadeklarowaną w przestrzeni nazw.

[!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
[!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Przykład
Następująca aplikacja korzysta z wcześniej zdefiniowanej biblioteki. Należy zauważyć, że typ, który jest zadeklarowany poza przestrzenią nazw jest `Test` tworzony, gdy nazwa nie jest kwalifikowana przez przestrzeń nazw. Należy również pamiętać, że w `Test` celu uzyskania `Goodspace`dostępu do typu w, nazwa przestrzeni nazw jest wymagana.

[!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
[!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]