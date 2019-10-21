---
title: 'CA1412: Mark ComSource Interfaces jako IDispatch | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 86dc7042a48faa200ef9c360829b1756bc261ab0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652734"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Oznacz interfejsy ComSource jako IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>, a co najmniej jeden określony interfejs nie jest oznaczony atrybutem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> ustawionym na wartość `InterfaceIsDispatch`.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> służy do identyfikowania interfejsów zdarzeń, które Klasa uwidacznia dla klientów Component Object Model (COM). Te interfejsy muszą być uwidocznione jako `InterfaceIsIDispatch`, aby umożliwić klientom Visual Basic 6, otrzymywanie powiadomień o zdarzeniach. Domyślnie, jeśli interfejs nie jest oznaczony atrybutem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, zostanie uwidoczniony jako podwójny interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać lub zmodyfikować atrybut <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, aby jego wartość była równa InterfaceIsIDispatch dla wszystkich interfejsów, które są określone przy użyciu atrybutu <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano klasę, w której jeden z interfejsów narusza regułę.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1408: Nie używaj wartości ClassInterfaceType dla elementu AutoDual](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz też
 [Instrukcje: wywoływanie zdarzeń obsłużonych przez obiekt UJŚCIA com](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [współpracujący z niezarządzanym kodem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
