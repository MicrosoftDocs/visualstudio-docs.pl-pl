---
title: 'DA0001: Użyj StringBuilder do łączenia | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0d93de6ce901bfe4d72628f778b18420beb5ebee
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779509"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Używaj StringBuilder do łączenia

|||
|-|-|
|Identyfikator zasady|DA0001|
|Kategoria|Użycie .NET Framework|
|Metody profilowania|Sond<br /><br /> Oprzyrządowanie|
|Komunikat|Rozważ użycie StringBuilder dla łączenia ciągów|
|Typ komunikatu|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania metody System. String. Concat są znaczną częścią danych profilowania. Rozważ użycie klasy <xref:System.Text.StringBuilder> do konstruowania ciągów z wielu segmentów.

## <a name="rule-description"></a>Opis reguły
 Obiekt <xref:System.String> jest niezmienny. W związku z tym wszystkie modyfikacje ciągu tworzą nowy obiekt String i wyrzucanie elementów bezużytecznych. Takie zachowanie jest takie samo, niezależnie od tego, czy wywoływana jest metoda String. Concat jawnie, czy też użyto operatorów łączenia ciągów, takich jak + lub + =. Wydajność programu można zmniejszyć, jeśli te metody są często wywoływane, na przykład gdy znaki są dodawane do ciągu w ścisłej pętli.

 Klasa StringBuilder jest obiektem modyfikowalnym i, w przeciwieństwie do System. String, większość metod w StringBuilder modyfikujących wystąpienie tej klasy zwraca odwołanie do tego samego wystąpienia. Można wstawiać znaki lub dołączać tekst do wystąpienia StringBuilder i usuwać lub zastępować znaki w wystąpieniu bez konieczności alokowania nowego wystąpienia i usuwania oryginalnego wystąpienia.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie **Lista błędów** , aby przejść do [widoku Szczegóły funkcji](../profiling/function-details-view.md) danych profilu próbkowania. Znajdź sekcje programu, które najczęściej używają łączenia ciągów. Użyj klasy StringBuilder do obsługi złożonych ciągów, w tym częstych operacji łączenia ciągów.

 Aby uzyskać więcej informacji na temat sposobu pracy z ciągami, sekcja [operacje na ciągach](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations) w [rozdziale 5 — Ulepszanie wydajności kodu zarządzanego](/previous-versions/msp-n-p/ff647790(v=pandp.10)) w bibliotece Microsoft Patterns and Practices.
