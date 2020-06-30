---
title: 'CA2103: Sprawdź zabezpieczenia bezwzględne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ade0d10e203752c7412929c6f5f44d9cbfaacfa6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521267"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Przejrzyj zabezpieczenia imperatywne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda używa imperatywnych zabezpieczeń i może konstruować uprawnienia za pomocą informacji o stanie lub wartości zwrotnych, które można zmienić, dopóki żądanie jest aktywne.

## <a name="rule-description"></a>Opis reguły
 Zabezpieczenia bezwzględne wykorzystują zarządzane obiekty do określania uprawnień i akcji zabezpieczeń podczas wykonywania kodu w porównaniu z zabezpieczeniami deklaratywnymi, które używają atrybutów do przechowywania uprawnień i akcji w metadanych. Zasadnicze zabezpieczenia są bardzo elastyczne, ponieważ można ustawić stan obiektu uprawnień i wybrać akcje zabezpieczeń przy użyciu informacji, które nie są dostępne do czasu uruchomienia. Ze względu na to elastyczność wiąże się z ryzykiem, że informacje o środowisku uruchomieniowym, które są używane do określenia stanu uprawnienia, nie pozostaną bez zmian, dopóki ta akcja jest aktywna.

 Należy używać zabezpieczeń deklaracyjnych wszędzie, gdzie to możliwe. Wymagania deklaracyjne są łatwiejsze do zrozumienia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zapoznaj się z niezależnymi wymaganiami dotyczącymi zabezpieczeń, aby upewnić się, że stan uprawnienia nie polega na informacjach, które mogą ulec zmianie, o ile uprawnienia są używane.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli uprawnienie nie polega na zmienianiu danych, można bezpiecznie pominąć ostrzeżenie z tej reguły. Jednak lepiej jest zmienić pierwotne zapotrzebowanie na jego deklaratywny odpowiednik.

## <a name="see-also"></a>Zobacz też
 [Zabezpieczanie](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [i modelowanie](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) wytycznych dotyczących kodowania
