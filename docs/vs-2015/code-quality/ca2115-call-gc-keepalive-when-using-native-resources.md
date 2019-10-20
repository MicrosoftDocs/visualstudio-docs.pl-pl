---
title: 'CA2115: Wywołaj metodę GC. Utrzymywanie aktywności w przypadku korzystania z zasobów natywnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e0aa10cc453919a2a79ee6d3d46db95c19d8756e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658699"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Wywołaj GC.KeepAlive gdy używasz zasobów natywnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Metoda zadeklarowana w typie z finalizatorem odwołuje się do <xref:System.IntPtr?displayProperty=fullName> lub <xref:System.UIntPtr?displayProperty=fullName> pola, ale nie wywołuje <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Wyrzucanie elementów bezużytecznych kończy obiekt, jeśli nie ma więcej odwołań do niego w kodzie zarządzanym. Niezarządzane odwołania do obiektów nie uniemożliwiają wyrzucania elementów bezużytecznych. Ta reguła wykrywa błędy, które mogą wystąpić, ponieważ kończy się działanie niezarządzanego zasobu, a wciąż jest on używany w kodzie niezarządzanym.

 Ta reguła zakłada, że pola <xref:System.IntPtr> i <xref:System.UIntPtr> przechowują wskaźniki do zasobów niezarządzanych. Ponieważ celem finalizatora jest zwolnienie niezarządzanych zasobów, reguła zakłada, że finalizator spowoduje zwolnienie niezarządzanego zasobu wskazywanego przez pola wskaźnika. Ta reguła zakłada również, że metoda odwołuje się do pola wskaźnika, aby przekazać niezarządzany zasób do kodu niezarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj wywołanie do <xref:System.GC.KeepAlive%2A> metody, przekazując bieżące wystąpienie (`this` w C# i C++) jako argument. Umieść wywołanie po ostatnim wierszu kodu, w którym obiekt musi być chroniony przed wyrzucaniem elementów bezużytecznych. Natychmiast po wywołaniu <xref:System.GC.KeepAlive%2A> obiekt jest ponownie uznawany za gotowy do wyrzucania elementów bezużytecznych przy założeniu, że nie istnieją żadne zarządzane odwołania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Ta reguła wykonuje pewne założenia, które mogą prowadzić do fałszywych wartości dodatnich. Możesz bezpiecznie pominąć ostrzeżenie z tej reguły, jeśli:

- Finalizator nie zwolni zawartości pola <xref:System.IntPtr> lub <xref:System.UIntPtr>, do którego odwołuje się metoda.

- Metoda nie przekazuje pola <xref:System.IntPtr> lub <xref:System.UIntPtr> do kodu niezarządzanego.

  Uważnie Przejrzyj inne komunikaty przed wyłączeniem ich. Ta zasada wykrywa błędy, które są trudne do odtworzenia i debugowania.

## <a name="example"></a>Przykład
 W poniższym przykładzie `BadMethod` nie obejmuje wywołania do `GC.KeepAlive` i w związku z tym narusza regułę. `GoodMethod` zawiera skorygowany kod.

> [!NOTE]
> Ten przykład jest pseudo kod, chociaż kod kompiluje i uruchamia, ostrzeżenie nie zostanie wyzwolone, ponieważ zasób niezarządzany nie został utworzony ani zwolniony.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName><xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Wzorzec Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
