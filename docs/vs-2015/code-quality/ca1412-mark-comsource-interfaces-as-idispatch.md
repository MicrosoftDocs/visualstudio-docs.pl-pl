---
title: 'CA1412: Oznacz interfejsy ComSource jako IDispatch | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 59fec1fddb16296f1238deb5c2f9bbf0c350cdd2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794934"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Oznacz interfejsy ComSource atrybutem IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ jest oznaczony za pomocą <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atrybut i co najmniej jeden określony interfejs nie jest oznaczony atrybutem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> ustawioną wartość atrybutu `InterfaceIsDispatch` wartość.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> Służy do identyfikowania interfejsów zdarzeń, które klasa udostępnia klientom Component Object Model (COM). Interfejsy te muszą być widoczne jako `InterfaceIsIDispatch` aby umożliwić klientom Visual Basic 6 COM otrzymywać powiadomienia o zdarzeniach. Domyślnie, jeśli interfejs nie jest oznaczony atrybutem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atrybutu, jest ona uwidoczniona jako podwójnego interfejsu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać lub zmodyfikować <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atrybutu tak, aby jego wartość jest równa InterfaceIsIDispatch dla wszystkich interfejsów, które są określone za pomocą <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje klasę, gdy jeden z interfejsów narusza regułę.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Wywoływanie zdarzeń obsługiwanych przez obiekty Sink modelu COM](http://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [współdziałanie z niezarządzanego kodu](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
