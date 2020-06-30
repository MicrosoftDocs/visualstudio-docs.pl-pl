---
title: DA0017 — wysokie stawki stronicowania aktywnej pamięci na dysk | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06295c1b158fe25b481b2aa036f8448895c546f5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544706"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Intensywne stronicowanie aktywnej pamięci na dysk

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0017|
|Kategoria|Pamięć i stronicowanie|
|Metoda profilowania|Wszystko|
|Komunikat|Występuje wysoki wskaźnik stronicowania aktywnej pamięci na dysk. Aplikacja może być powiązana z pamięcią.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu zebrane w ramach uruchomienia profilowania wskazują, że jest duża częstotliwość stronicowania aktywnej pamięci do i z dysku podczas całego uruchomienia profilowania. Stawki stronicowania na tym poziomie zwykle mają wpływ na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez skorygowanie algorytmów. Może być również konieczne uwzględnienie wymagań dotyczących pamięci aplikacji.

## <a name="rule-description"></a>Opis reguły

> [!NOTE]
> Ta zasada informacyjna jest wyzwalana, gdy poziomy stronicowania aktywnej pamięci osiągną znaczną ilość. Gdy występuje bardzo wysoki poziom stronicowania, reguła ostrzegawcza [DA0014: niezwykle wysokie stawki stronicowania aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) .

 Nadmierne stronicowanie na dysku może być spowodowane brakiem pamięci fizycznej. Jeśli operacje stronicowania korzystają z dysku fizycznego, w którym znajduje się plik stronicowania, mogą spowolnić inne operacje na dysku zorientowanym na aplikacje na tym samym dysku.

 Strony są często odczytywane z dysku lub zapisywane na dysku w operacjach stronicowania zbiorczego. Liczba stron wyjściowych/s jest często znacznie większa niż liczba operacji zapisu stron/s, na przykład. Ponieważ strony wyjściowe/s zawierają również zmienione strony danych z pamięci podręcznej plików systemowych. Jednak nie zawsze można łatwo ustalić, który proces jest bezpośrednio odpowiedzialny za stronicowanie lub dlaczego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku [znaczniki](../profiling/marks-view.md) . Znajdowanie kolumny **pamięć \ strony/s** . Ustal, czy istnieją określone fazy wykonywania programu, w których operacje we/wy stronicowania są większe niż inne.

 Jeśli zbierasz dane profilu dla aplikacji ASP.NET w scenariuszu testowania obciążenia, spróbuj ponownie uruchomić test obciążenia na komputerze skonfigurowanym z dodatkową pamięcią fizyczną (lub pamięcią RAM).

 Należy rozważyć zmniejszenie alokacji pamięci przez skorygowanie algorytmów i uniknięcie interfejsów API intensywnie korzystających z pamięci, takich jak String. Concat i String. substring.
