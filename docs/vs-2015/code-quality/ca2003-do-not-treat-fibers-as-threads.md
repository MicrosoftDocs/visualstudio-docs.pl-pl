---
title: 'CA2003: nie Traktuj włókien jako wątków | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a8172490b267949686dd3390c85ed6d86531b192
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521177"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Nie traktuj włókien jak wątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Kategoria|Microsoft. niezawodność|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Zarządzany wątek jest traktowany jako wątek Win32.

## <a name="rule-description"></a>Opis reguły
 Nie przyjmij wątku zarządzanego jako wątku Win32. Jest to włókna. Środowisko uruchomieniowe języka wspólnego (CLR) będzie uruchamiać wątki zarządzane jako włókien w kontekście rzeczywistych wątków, które są własnością bazy danych SQL. Te wątki mogą być współużytkowane przez domeny aplikacji i nawet bazy danych w procesie SQL Server. Korzystanie z lokalnego magazynu wątków zarządzanych będzie działać, ale nie można używać magazynu lokalnego wątku niezarządzanego lub założono, że kod zostanie uruchomiony ponownie w bieżącym wątku systemu operacyjnego. Nie należy zmieniać ustawień, takich jak ustawienia regionalne wątku. Nie wywołuj CreateCriticalSection ani muteksu za pośrednictwem P/Invoke, ponieważ wymagają one, aby wątek, który przechodził blokadę, również zakończył blokadę. Ponieważ nie będzie to miało znaczenia w przypadku używania włókien, sekcje krytyczne Win32 i muteksy będą bezużyteczny w programie SQL Server. Można bezpiecznie użyć większości stanu w zarządzanym obiekcie system. Thread. Obejmuje to magazyn lokalny wątku zarządzanego i kulturę bieżącego interfejsu użytkownika (UI) wątku. Jednak ze względu na model programowania nie będzie można zmienić bieżącej kultury wątku w przypadku korzystania z programu SQL Server. zostanie to wymuszone za pomocą nowego uprawnienia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Sprawdź użycie wątków i odpowiednio zmień kod.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie należy pomijać tej reguły.
