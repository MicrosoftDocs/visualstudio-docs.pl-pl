---
title: 'CA2006: Użyj elementu SafeHandle do hermetyzacji zasobów natywnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 394fafb0c9185a5e11ba759a5b873236956cf25b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652215"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Użyj SafeHandle, aby hermetyzować zasoby natywne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategoria|Microsoft. niezawodność|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Kod zarządzany używa <xref:System.IntPtr> w celu uzyskania dostępu do zasobów natywnych.

## <a name="rule-description"></a>Opis reguły
 Użycie `IntPtr` w kodzie zarządzanym może wskazywać na potencjalny problem z zabezpieczeniami i niezawodnością. Wszystkie zastosowania `IntPtr` muszą zostać sprawdzone, aby określić, czy w tym miejscu jest wymagane użycie <xref:System.Runtime.InteropServices.SafeHandle> lub podobnej technologii. Jeśli `IntPtr` reprezentuje jakiś zasób natywny, taki jak pamięć, dojście do pliku lub gniazdo, kod zarządzany jest uznawany za własny. Jeśli zarządzany kod jest właścicielem zasobu, musi również zwolnić natywne skojarzone z nim zasoby, ponieważ nie spowoduje to powstania wycieku zasobów.

 W takich scenariuszach istnieją również problemy z zabezpieczeniami lub niezawodnością, jeśli dostęp wielowątkowy jest dozwolony do `IntPtr` i do zwolnienia zasobu reprezentowanego przez `IntPtr`. Te problemy obejmują odtwarzanie wartości `IntPtr` w wydaniu zasobów podczas jednoczesnego korzystania z zasobu w innym wątku. Może to spowodować sytuacje wyścigu, w których jeden wątek może odczytywać lub zapisywać dane skojarzone z niewłaściwym zasobem. Na przykład, jeśli typ przechowuje dojście systemu operacyjnego jako `IntPtr` i umożliwia użytkownikom wywoływanie zarówno **zamknięcia** , jak i innej metody, która używa tego uchwytu jednocześnie i bez pewnego rodzaju synchronizacji, kod ma problem z odtwarzaniem obsługi.

 Ten problem z odtwarzaniem obsłudze może spowodować uszkodzenie danych i często lukę w zabezpieczeniach. `SafeHandle` i jej klasy równorzędnej <xref:System.Runtime.InteropServices.CriticalHandle> zapewniają mechanizm hermetyzowania natywnego uchwytu do zasobu, dzięki czemu można uniknąć takich problemów z wątkami. Ponadto można użyć `SafeHandle` i jej klasy równorzędnej `CriticalHandle` w przypadku innych problemów z wątkami, na przykład w celu starannej kontroli okresu istnienia zarządzanych obiektów, które zawierają kopię natywnego uchwytu wywołań metod natywnych. W takiej sytuacji często można usunąć wywołania `GC.KeepAlive`. Narzuty wydajnościowe Thay naliczane w przypadku używania `SafeHandle` i, w mniejszym stopniu, `CriticalHandle`, często można je zmniejszyć poprzez staranne projektowanie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Przekonwertuj użycie `IntPtr` na `SafeHandle`, aby bezpiecznie zarządzać dostępem do zasobów natywnych. Przykłady można znaleźć w temacie <xref:System.Runtime.InteropServices.SafeHandle> Reference.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie należy pomijać tego ostrzeżenia.

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable>
