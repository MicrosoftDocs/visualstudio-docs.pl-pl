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
ms.openlocfilehash: 5685ad7a760e00392b5f9684cdf399ee320d4a0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540260"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Oznacz interfejsy ComSource atrybutem IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ jest oznaczony <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atrybutem, a co najmniej jeden określony interfejs nie jest oznaczony <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atrybutem ustawionym na `InterfaceIsDispatch` wartość.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> służy do identyfikowania interfejsów zdarzeń, które Klasa uwidacznia dla klientów Component Object Model (COM). Te interfejsy muszą być uwidocznione jako, `InterfaceIsIDispatch` Aby umożliwić klientom Visual Basic 6 com otrzymywanie powiadomień o zdarzeniach. Domyślnie, jeśli interfejs nie jest oznaczony <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atrybutem, zostanie uwidoczniony jako podwójny interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać lub zmodyfikować atrybut, <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> tak aby jego wartość była równa InterfaceIsIDispatch dla wszystkich interfejsów, które są określone przy użyciu <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano klasę, w której jeden z interfejsów narusza regułę.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz też
 [Instrukcje: wywoływanie zdarzeń obsłużonych przez obiekt UJŚCIA com](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [współpracujący z niezarządzanym kodem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
