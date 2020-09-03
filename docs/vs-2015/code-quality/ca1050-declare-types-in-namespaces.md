---
title: 'CA1050: deklaruj typy w przestrzeniach nazw | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0a4dcc53fac7dc9b7e189686a3b32e2fb4fd030
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539597"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Deklaruj typy w przestrzeniach nazw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Kategoria|Microsoft. Design|
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

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja korzysta z wcześniej zdefiniowanej biblioteki. Należy zauważyć, że typ, który jest zadeklarowany poza przestrzenią nazw jest tworzony, gdy nazwa `Test` nie jest kwalifikowana przez przestrzeń nazw. Należy również pamiętać, że w celu uzyskania dostępu do `Test` typu w `Goodspace` , nazwa przestrzeni nazw jest wymagana.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
