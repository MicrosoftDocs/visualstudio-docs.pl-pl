---
title: 'CA2112: zabezpieczone typy nie powinny ujawniać pól | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4267b4f55f78106a4d1e8f3b2f9b296be9ddf618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546539"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Zabezpieczone typy nie powinny ujawniać pól
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera pola publiczne i jest zabezpieczony przez wymagania dotyczące [łącza](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Opis reguły
 Jeśli kod ma dostęp do wystąpienia typu zabezpieczonego przez żądanie łącza, kod nie musi spełniać zapotrzebowania na łącza, aby uzyskać dostęp do pól typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Ustaw pola jako niepubliczne i Dodaj właściwości publiczne lub metody, które zwracają dane pola. LinkDemand kontroli zabezpieczeń typów ochrony dostępu do właściwości i metod typu. Jednak zabezpieczenia dostępu kodu nie mają zastosowania do pól.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Zarówno w przypadku problemów z zabezpieczeniami, jak i w dobrym projekcie należy rozwiązać naruszenia, wprowadzając pola publiczne jako publiczne. Możesz pominąć ostrzeżenie z tej reguły, jeśli pole nie zawiera informacji, które powinny pozostać zabezpieczone i nie zależą od zawartości pola.

## <a name="example"></a>Przykład
 Poniższy przykład składa się z typu biblioteki ( `SecuredTypeWithFields` ) z niezabezpieczonymi polami, typu (), `Distributor` który może tworzyć wystąpienia typu biblioteki i wycofać przekazanie wystąpień do typów, nie ma uprawnień do ich tworzenia i kod aplikacji, który może odczytywać pola wystąpienia, mimo że nie ma uprawnień zabezpieczających typ.

 Poniższy kod biblioteki narusza regułę.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Przykład
 Aplikacja nie może utworzyć wystąpienia z powodu żądania linku chroniącego zabezpieczony typ. Poniższa klasa umożliwia aplikacji uzyskanie wystąpienia typu zabezpieczonego.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Przykład
 W poniższej aplikacji przedstawiono, jak bez uprawnienia dostępu do metod zabezpieczonych typów kod może uzyskać dostęp do jego pól.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Tworzenie wystąpienia elementu SecuredTypeWithFields.** 
 **Pola zabezpieczonego typu: 22, 33** 
 Trwa **Zmienianie pola zabezpieczonego typu...** 
 **Buforowane pola obiektu: 99, 33**
## <a name="related-rules"></a>Powiązane reguły
 [CA1051: Nie deklaruj widocznych pól w wystąpieniach](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Zobacz też
 [Link wymaga](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [danych i modelowania](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
