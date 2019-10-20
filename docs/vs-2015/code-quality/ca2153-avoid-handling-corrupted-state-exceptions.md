---
title: 'CA2153: zapobiegaj obsłudze wyjątków uszkodzonego stanu | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9d4ca2668f2d6241e9a3cca88b4722ee5348abc3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667410"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Unikaj obsługiwania uszkodzonych wyjątków stanu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 [Wyjątki uszkodzonych Stanów (rozszerzenie klienta)](https://msdn.microsoft.com/magazine/dd419661.aspx) wskazują, że uszkodzenie pamięci istnieje w procesie. Ich przechwycenie zamiast zezwalania na awarię procesu może prowadzić do luk w zabezpieczeniach, jeśli osoba atakująca może wykorzystać lukę w uszkodzonym regionie pamięci.

## <a name="rule-description"></a>Opis reguły
 Rozszerzenie klienta wskazuje, że stan procesu został uszkodzony i nie został przechwycony przez system. W scenariuszu uszkodzenia stanu ogólna procedura obsługi przechwytuje wyjątek tylko wtedy, gdy oznaczy metodę przy użyciu odpowiedniego atrybutu `HandleProcessCorruptedStateExceptions`. Domyślnie [środowisko uruchomieniowe języka wspólnego (CLR)](https://msdn.microsoft.com/library/8bs2ecf4.aspx) nie wywoła obsługi catch dla rozszerzeń klienta.

 Umożliwienie procesowi awarii bez przechwycenia tych rodzajów wyjątków jest najbezpieczniejsza opcja, ponieważ nawet kod rejestrowania może spowodować, że atakujący mogą wykorzystać błędy uszkodzeń pamięci.

 To ostrzeżenie jest wyzwalane podczas przechwytywania rozszerzeń klienta z użyciem ogólnej procedury obsługi, która przechwytuje wszystkie wyjątki, takie jak catch (Exception) lub catch (bez specyfikacji wyjątku).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, należy wykonać jedną z następujących czynności:

 1. Usuń atrybut `HandleProcessCorruptedStateExceptions`. Spowoduje to przywrócenie domyślnego zachowania środowiska uruchomieniowego, w którym rozszerzeń klienta nie są przenoszone do obsługi catch.

 2. Usuń ogólny program obsługi catch w preferencjach obsługi, które przechwytują określone typy wyjątków.  Może to obejmować rozszerzeń klienta przy założeniu, że kod procedury obsługi może bezpiecznie obsłużyć je (bardzo rzadki).

 3. Ponownie zgłoś rozszerzenie klienta w programie obsługi catch, który zapewnia, że wyjątek jest przesyłany do obiektu wywołującego, i spowoduje zakończenie działania procesu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykład pseudo kodu

### <a name="violation"></a>Krocz
 Poniższy pseudo kodu ilustruje wzorzec wykryty przez tę regułę.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Rozwiązanie 1
 Usunięcie atrybutu HandleProcessCorruptedExceptions gwarantuje, że wyjątki nie będą obsługiwane.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Rozwiązanie 2
 Usuń ogólny program obsługi catch i Przechwyć tylko określone typy wyjątków.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Rozwiązanie 3
 Ponownie Zgłoś wyjątek.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```
