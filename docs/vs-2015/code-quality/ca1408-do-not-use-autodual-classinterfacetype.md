---
title: 'CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 88d23ee703b482813ad0a5401e9dea7adf9a063c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705704"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny Component Object Model (COM) jest oznaczony za pomocą <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> ustawioną wartość atrybutu `AutoDual` wartość <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Opis reguły
 Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie jeśli <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut nie zostanie określony, używany jest interfejs tylko do wysyłki.

 O ile nie jest oznaczony jako inaczej, wszystkie typy nierodzajowymi publiczne są widoczne dla modelu COM; wszystkie typy niepublicznych i ogólny są niewidoczne dla modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić wartość <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu `None` wartość <xref:System.Runtime.InteropServices.ClassInterfaceType> i jawnie definiują interfejs.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, jeśli nie jest pewne, czy układu typu i jego typów podstawowych nie spowoduje zmiany w przyszłych wersjach.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia klasę, która narusza regułę i ponownej deklaracji klasy, aby używać interfejsu jawnego.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: Oznacz interfejsy ComSource jako IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Zobacz też
 [Wprowadzenie interfejsu klasy](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [kwalifikowanie typów .NET do międzyoperacyjności](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [współdziałanie z niezarządzanego kodu](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
